var express = require('express');
var router = express.Router();

var mongoose = require('mongoose');
mongoose.connect('mongodb://alfaysal:alfaysal@ds143388.mlab.com:43388/alfaysal').then(
    function () {
        console.log("connected")
    }
).catch(
    function (error) {
        console.log(error.message)
    });
var eva = mongoose.Schema('evaluations', {
    Evaluation: String,
    reason: String,
});

var form = new mongoose.Schema({
    name: String,
    number: String,
    email: String,
    tourism: String,
    compan: String,
    trip: String,
})

/* GET home page. */
router.get('/home', function (req, res) {
    res.render('face');
});

router.get('/places', function (req, res) {
    res.render('tourism');
});

router.get('/reservation', function (req, res) {
    res.render('reservations');
});

router.get('/opinions', function (req, res) {
    res.render('opinions');
});

router.get('/evaluation', function (req, res) {
    evaluations.find(function (error, evaluations) {
        res.json(evaluations);
    })

});

router.post('/reservation', function (req, res) {
    console.log("text")

    console.log(res.param());

    console.log("trying!")
    var newForm = req.param('form');
    var databaseForm = new form(newForm)

    databaseForm.save().then(function () {
        alert("save")
    });
})
