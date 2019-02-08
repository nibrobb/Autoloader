var loadInterval = setInterval(mTimer, 500);
var mVar = 0;

var urlString = window.location.href;

var mIdentifier;
var mMarketplace;

function parseURLParams(url) {
    var queryStart = url.indexOf("?") + 1,
        queryEnd   = url.indexOf("#") + 1 || url.length + 1,
        query = url.slice(queryStart, queryEnd - 1),
        pairs = query.replace(/\+/g, " ").split("&"),
        parms = {}, i, n, v, nv;

    if (query === url || query === "") return;

    for (i = 0; i < pairs.length; i++) {
        nv = pairs[i].split("=", 2);
        n = decodeURIComponent(nv[0]);
        v = decodeURIComponent(nv[1]);

        if (!parms.hasOwnProperty(n)) parms[n] = [];
        parms[n].push(nv.length === 2 ? v : null);
    }
    return parms;
}

urlParams = parseURLParams(urlString);

mMarketplace = urlParams['marketid'];
mIdentifier = urlParams['identifier'];

function mTimer() {

    //Pris linje
    new Ajax.Updater('instrumentcontainer', '/mux/ajax/marknaden/aktiehemsidan/instrumentcontainer.html', { parameters: {identifier: mIdentifier, marketplace : mMarketplace, update: 'update'}});

    //Siste handler
    new Ajax.Updater('avslut', '/mux/ajax/marknaden/aktiehemsidan/avslut.html', {parameters: 'identifier=' + mIdentifier + '&marketplace=' + mMarketplace + '&containerid=avslut'});

    //Ordredybde
    new Ajax.Updater('orderdjup', '/mux/ajax/marknaden/aktiehemsidan/orderdjup.html', {parameters:'identifier=' + mIdentifier + '&marketplace=' + mMarketplace + '&orderdjupsantal=5&country=Norge'});
    
    document.title = "Autoloader activated!";
}