---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/geoPointToDmsV1/"
title: "Convert GeoPoint to DMS"
---
# Convert GeoPoint to DMS

Supported in: Batch, Faster, Streaming. Converts a GeoPoint to a geospatial coordinate string in degrees, minutes, seconds (DMS) format in accordance with a user-chosen format. Possible formats are DDD°MM'SS"H and DDDMMSSssH. Expression categories: Geospatial. Declared arguments. Format: Outputs GeoPoints to either DDD°MM'SS"H or DDDMMSSssH. Enum<DDDMMSSssH, DDD°MM'SS.sss"H> GeoPoint: GeoPoint to convert to DMS. Expression<GeoPoint> Output type: String. Examples. Example 1: Base case. Argument values: Format: DDD_DEGREE_MM_MINUTE_SS_SECOND_sss_H. GeoPoint: point. pointOutput { latitude: -20.0, longitude: 80.0, } 020°00'00.000"S 080°00'00.000"E. { latitude: 40.13, longitude: 60.32, } 040°07'48.000"N 060°19'12.000"E. { latitude: -45.32142, longitude: 163.2412, } 045°19'17.112"S 163°14'28.320"E. Example 2: Base case. Argument values: Format: DDD_MMSSss_H. GeoPoint: point. pointOutput { latitude: 40.13626, longitude: 60.12732, } 040081053N 060073835E. { latitude: -20.0, longitude: 80.0, } 020000000S 080000000E. { latitude: -45.32142, longitude: 163.2412, } 045191711S 163142831E. Example 3: Null case. Argument values: Format: DDD_MMSSss_H. GeoPoint: point. pointOutput null. null.
