# Geocoding

By default, geocoding uses simple single input field geocoding:

    client.geocode({ text: "920 SW 3rd Ave, Portland, OR 97201" }, function (err, result) {
      if (err) {
        console.error("ERROR: " + err);
      } else {
        console.log("Found it at " + result.locations[0].feature.geometry.y + ", " result.locations[0].feature.geometry.x);
      }
    });

## Simple Geocoding

Simple geocoding is the same as the default `geocode` method:

    client.geocode.simple({ text: "920 SW 3rd Ave, Portland, OR 97201" }, function (err, result) {
      if (err) {
        console.error("ERROR: " + err);
      } else {
        console.log("Found it at " + result.locations[0].feature.geometry.y + ", " result.locations[0].feature.geometry.x);
      }
    });

## Reverse Geocoding

      client.geocode.reverse({ location: "-122.67633658436517,45.5167324388521" }, function (err, result) {
      if (err) {
        console.error("ERROR: " + err);
      } else {
        console.log("Found it at " + result.address.Address + ", " + result.address.City);
      }
    });

## Batch Geocoding

Batch geocoding requires authentication.

    var client = new Geoservices();
    
    client.authentication.authenticate('username', 'password', { /* optional options */ }, callback);

Once you are authenticated, you can use batch geocoding.

    var batch = new client.geocode.Batch();
    
    // add addresses to geocode
    batch.geocode("123 Fake Street");
    batch.geocode("456 Other Street");
    
    // run the batch
    batch.run(function (err, results) {
      console.dir(results);
    });
