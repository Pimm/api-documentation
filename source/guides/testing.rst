Testing the Mollie API
======================
During the process of building your integration, it is important to properly test it. As briefly
explained in our :doc:`authentication guide </guides/authentication>`, you can access the test mode
of the Mollie API in two ways: by using the *Test API key*, or, if you're using organization access
tokens or app tokens, by providing the ``testmode`` parameter in your API request.

Any payments or other resources you create in test mode are completely isolated from your live mode
data. Going back and forth between test and live mode is as easy as switching out the API key - or
toggling the ``testmode`` parameter in case of the other authentication methods.

Test mode checkout screen
-------------------------
When creating payments or orders in test mode, the regular checkout screen will be replaced by a test mode
checkout screen. Most test mode payment resources will feature a ``checkout`` URL just like in live
mode, which then allows you to walk through the payment process without spending actual money. You
can try out different payment statuses and see whether your integration handles it correctly.

For test mode *recurring* payments, the resource will not contain a ``checkout`` URL, because these
payments are executed without any interaction of your customer. Instead, a ``changePaymentState``
URL is added, which allows you to set the final payment state for these payments.

For paid test mode payments the resource will also include the ``changePaymentState`` URL which allows you to create a
refund or chargeback for that payment from the checkout screen. This can be used to test refund and chargeback
functionality.

Apart from the hosted payment pages and the fact that test mode payments are created instead of real
ones, the Mollie API behaves almost identical in both environments. This includes calling your
:doc:`webhook </guides/webhooks>`. Just make sure to start using live mode when your site goes public,
or your customers will get a free ride.
