This is an example readme.
About
This is a train scheduler app. it stores data in firebase and does quick maths for time.

Demo
https://nathaniel-du.github.io/Train-Scheduler/.

Requirements
dependencies of the application. 
Firebase

$(document).ready(function(){
    var firebaseConfig = {
        apiKey: "AIzaSyCbxb9H18TMp-0p-hy64jzx-vIx6pHXCCY",
        authDomain: "train-time-9c066.firebaseapp.com",
        databaseURL: "https://train-time-9c066.firebaseio.com",
        projectId: "train-time-9c066",
        storageBucket: "train-time-9c066.appspot.com",
        messagingSenderId: "891495617972",
        appId: "1:891495617972:web:368a720447d210b8888ee1"
    };
    firebase.initializeApp(firebaseConfig);

    Moment

    database.ref().on("child_added", function(childSnapshot) {
        var nextArr;
        var minAway;
        // first train comes before now
        var firstTrainNew = moment(childSnapshot.val().firstTrain, "hh:mm").subtract(1, "years");
        // Difference between the current and firstTrain
        var diffTime = moment().diff(moment(firstTrainNew), "minutes");
        var remainder = diffTime % childSnapshot.val().frequency;
        // Minutes until next train
        var minAway = childSnapshot.val().frequency - remainder;
        // Next train time
        var nextTrain = moment().add(minAway, "minutes");
        nextTrain = moment(nextTrain).format("hh:mm");


technologies used:

Bootstrap
jQuery
firebase
javascript