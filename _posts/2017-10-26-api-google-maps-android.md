---
layout: post
title: API DO GOOGLE MAPS EM PROJETO ANDROID
---

Para habilitar a comunicação com a API do google, você precisará de uma chave *(API_KEY)*. 

E para consegui-la: [veja aqui](https://developers.google.com/maps/documentation/static-maps/get-api-key)

Adicione ao seu build gradle: ``` compile 'com.google.android.gms:play-services-maps:11.0.4' ```

	
Faça  a sua classe (MinhaClasseActivity) extender *FragmentActivity*  e implementar *OnMapReadyCallback*;  

Com isso, você poderá sobreescrever o método *onMapReady*(GoogleMap googleMap). 
E nele 
```java
Map.addMarker(new MarkerOptions().position(p1).title("Titulo"));
mMap.moveCamera(CameraUpdateFactory.newLatLng(p1));```
	
Para adicionar um ponto de localização e mover a câmera do mapa a ele.

**EXTRA**: Percebe-se que a localização está na forma de Longitude e Latitude, e geralmente aplicações transitam o endereço como uma string. Portanto, para converter essa string em coordenadas geo. use um método conversor com GeoCoder.

```java
Geocoder coder = new Geocoder(this);
List<Address> address = new ArrayList<>();
LatLng p1 = null;

try {
   try {
       address = coder.getFromLocationName(enderecoStr,5);
   } catch (IOException e) {
       e.printStackTrace();
   }
   if (address==null) {
   }
   Address location=address.get(0);
   location.getLatitude();
   location.getLongitude();

   p1 = new LatLng((double)location.getLatitude(),
           (double)location.getLongitude());
}catch (Exception e){

}
```	

