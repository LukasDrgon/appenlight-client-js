errormator_client_javascript
============================

.. image:: https://errormator.com/static/images/logos/js_small.png
   :alt: JS Logo


**WARNING THIS IS STILL ALPHA CODE - USE AT YOUR OWN RISK**


Installation and Setup
======================

**Load the script asynchroneously**::

    var init_errormator = function () {
          var err_client = new Errormator();
          window.err_client = err_client;
          err_client.init({
              api_key:'PUBLIC_API_KEY',
              window_on_error: 1 // enable to hook to window.onerror
          });
          // setting request info is completly optional
          err_client.setRequestInfo({
              server:'servername',
              username:'i_am_mario',
              ip: "127.0.0.1",
              request_id:"server_generated_uuid"
          });
    };
    //  load the script asynchroneously
    var emator = document.createElement('script');
    emator.type = 'text/javascript';
    emator.async = true;
    emator.onload = emator.onreadystatechange = init_errormator;
    emator.src = "/path/to/errormator-client.js";
    var p = document.getElementsByTagName('script')[0];
    p.parentNode.insertBefore(emator, p);


**EXAMPLE USAGE**::

    // wait for client to load to test error
    setTimeout(function(){
        try{
          1 + vcvx1;
        }catch(exc){
          err_client.grabError(exc);
        }
    },5000);