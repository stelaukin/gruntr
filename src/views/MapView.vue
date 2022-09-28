<!-- MAPS API KEY -->
<!-- *************************************** --> 

<!-- MAP implentation using vue3-google-map -->
<template>
  <div>

    <div>

      <h3 v-if="show">
        Move the map and click on a toilet location to find out more information.
      </h3>

    </div>


    <GoogleMap style="width: 100%; height: 100vh" :center="center" :zoom="10">
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
              <li>Accessible: {{ pos.accessible }}</li>
              <li>Baby Change: {{ pos.baby }}</li>
              <li>{{ pos.open }}</li>
            </ul>
          </InfoWindow>
        </Marker>
      </MarkerCluster>
    </GoogleMap>
    <!-- <ul>
      <li v-for="toilet in toilets" v-bind:key="toilet.FacilityID">
        {{ toilet.Name }}
      </li>
    </ul> -->
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
      show: true
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
      accessible: t.Accessible,
      baby: t.BabyChange,
      open: t.OpeningHours,
    }));

    const center = { lat: -41.93, lng: 147.49 };
    return { center, markerPos };
  },
});
</script>