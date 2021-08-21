---
layout: single
title: "GPS Tracker module development."
---

# GPS Tracker 앱을 계발한 후 소감 #
여러 에러 사항들로 인해 6개월이나 질질 끌었던 GPS 앱을 완성했다.
안드로이드 스튜디오를 이용하여 코드를 짰으며 파이어베이스의 리얼타임베이스를 이용하여 데이터를 저장했다.
# 주요 에러 사항 #
1. snapshot 변수 에러(snapshot -> snapshot)
                            public void onDataChange(@NonNull DataSnapshot snapshot) {
                                DO data = snapshot.getValue(DO.class);
                                LatLng point = new LatLng(Double.parseDouble(data.getLatitude()), Double.parseDouble(data.getLongitude()));
                                mMap.addMarker(new MarkerOptions().position(point).title("Marker"));
                                mMap.moveCamera(CameraUpdateFactory.newLatLng(point));
                                mMap.moveCamera(CameraUpdateFactory.zoomTo(17.5f));
                            }

2. release 키 수정 (디버그 키 등록 뿐만 아니라 릴리즈 키도 직접 입력해야 함)
C:\Users\10del\AndroidStudioProjects\FindYou\app\src\release\res\values

3. SHA-1 키 입력 (구글 API에 디버그와 함께 등록해줘야함)
cmd
C:\Users\10del\AndroidStudioProjects>keytool -v -list -keystore test.jks

4. GPS PROVIDER와 함께 코드 추가
 ACCESS_COARSE_LOCATION 
manager.requestLocationUpdates(LocationManager.NETWORK_PROVIDER, 1000, 1, mLocationListener);



