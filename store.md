---
layout: page
title: Store
subtitle: PDFs and Guitar Pro files
---


![ ]({{ site.baseurl }}/images/zombie-strumming-thumbnail.png){: .mx-auto.d-block :}

<button class="btn btn-success btn-lg get-started-btn" data-checkout-mode="payment" data-price-id="price_1KpIwQF1bxnTbGQ8PDTJuDMy">50% off Sale: <del>$5.00</del> $2.50</button>
<p>A practice guide for strumming along to the song "Zombie" by The Cranberries. 1 PDF and 1 Guitar Pro file of all 10 strumming patterns (from easy to hard). You can also send at least .0001 BTC to <a href="http://cash.app/$chrispaulintheory">$chrispaulintheory</a> via Cash App and I'll email you the PDF and GP files.</p>

<button class="btn btn-success btn-lg get-started-btn" data-checkout-mode="payment" data-price-id="price_1KqnQCF1bxnTbGQ8MHxElhjk">$2.50</button>
<p>A practice guide for the bass part on Hotel California. 8 difficulty levels. 1 PDF and 1 Guitar Pro file. You can also send at least .0001 BTC to <a href="http://cash.app/$chrispaulintheory">$chrispaulintheory</a> via Cash App and I'll email you the PDF and GP files.</p>

<script>
  var PUBLISHABLE_KEY = 'pk_live_51KoWpmF1bxnTbGQ8Qv9jTifc1EY19iO9tQBeOwZR8fuZ1ChM2UHO3reof9Znjq8TzUrwrnmHYg9wftymr1AJFIac00ItpelA07';
  
  // Replace with the domain you want your users to be redirected back to after payment
  var DOMAIN = location.href.replace(/\/+$/, '');
  var stripe = Stripe(PUBLISHABLE_KEY);

  // Handle any errors from Checkout
  var handleResult = function (result) {
    if (result.error) {
      var displayError = document.getElementById('error-message');
      displayError.textContent = result.error.message;
    }
  };

  document.querySelectorAll('button').forEach(function (button) {
    button.addEventListener('click', function (e) {
      this.disabled = true;
      var mode = e.target.dataset.checkoutMode;
      var priceId = e.target.dataset.priceId;
      var items = [{ price: priceId, quantity: 1 }];

      // Make the call to Stripe.js to redirect to the checkout page
      // with the sku or plan ID.
      stripe
        .redirectToCheckout({
          mode: mode,
          lineItems: items,
          successUrl:
            DOMAIN + '_' + priceId + '?session_id={CHECKOUT_SESSION_ID}',
          cancelUrl:
            DOMAIN + '_canceled?session_id={CHECKOUT_SESSION_ID}',
        })
        .then(handleResult);
    });
  });
</script>