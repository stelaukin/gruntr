<!-- MAPS API KEY -->
<!-- AIzaSyAuDdI55xkd_BCgEmjCz-xkFzrPOIqBjHQ --> 


<template>
  <div>
    <GoogleMap style="width: 100%; height: 100vh" :center="center" :zoom="7">
      <!-- <Marker :options="{ position: center }" /> -->
      <MarkerCluster>
        <Marker
          v-for="pos in markerPos"
          v-bind:key="pos.id"
          v-bind:options="pos"
        >
          <InfoWindow style="color: black">
            <ul>
              <li>{{ pos.title }}</li>
              <li>{{ pos.address }}</li>
              <li>{{ pos.town }}</li>
            </ul>
          </InfoWindow>
        </Marker>
      </MarkerCluster>
    </GoogleMap>
    <ul>
      <li v-for="toilet in toilets" v-bind:key="toilet.FacilityID">
        {{ toilet.Name }}
      </li>
    </ul>
  </div>
</template>
  
<script>
import { defineComponent } from "vue";
import { GoogleMap, Marker, MarkerCluster, InfoWindow } from "vue3-google-map";
//   import all toilt data from file
import rawToilets from "../assets/data/toiletsTas.json";
export default defineComponent({
  data() {
    return {
      toilets: rawToilets,
    };
  },
  components: { GoogleMap, Marker, MarkerCluster, InfoWindow },
  setup() {
    // turns raw data into google map location data using vue3-google-map package
    const markerPos = rawToilets.map((t) => ({
      position: { lat: Number(t.Latitude), lng: Number(t.Longitude) },
      label: t.Name.charAt(0),
      id: t.FacilityID,
      title: t.Name,
      address: t.Address1,
      town: t.Town,
    }));

    const center = { lat: -41.93, lng: 147.49 };
    return { center, markerPos };
  },
});
</script>