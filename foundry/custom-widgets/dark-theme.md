---
source_url: "https://www.palantir.com/docs/foundry/custom-widgets/dark-theme/"
title: "Dark theme support"
---
# Dark theme support

Custom widgets can use the prefers-color-scheme ↗ CSS media feature to detect the color-scheme ↗ of the parent application and apply appropriate styles. 1 2 3 4 5 6 7 8 9 .container { background: white; } @media (prefers-color-scheme: dark) { .container { background: black; } } Additionally, the window.matchMedia() ↗ method can be used to detect the color scheme from JavaScript, for example to apply a theme to a component library. 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 const Component: React.FC = () => { const isDarkTheme = useDarkTheme(); return <Theme appearance={isDarkTheme ? "dark" : "light"}>...</Theme>; }; const useDarkTheme = () => useMediaQuery("(prefers-color-scheme: dark)"); const useMediaQuery = (query: string) => { const [matches, setMatches] = useState(false); const handleChange = (e: MediaQueryListEvent) => setMatches(e.matches); useEffect(() => { const mediaQueryList = window.matchMedia(query); setMatches(mediaQueryList.matches); mediaQueryList.addEventListener("change", handleChange); return () => { mediaQueryList.removeEventListener("change", handleChange); }; }, [query]); return matches; };
