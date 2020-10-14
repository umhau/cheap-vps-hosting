# cheap-vps-hosting
The code to make the cheap vps hosting idea come alive

# architecture

Rent a VPN, tunnel all traffic through that. Keep the IP address for myself. When I get big enough for a rack, put openbsd on something that can handle the traffic and use that as a firewall.

# notes

- Don't forget to geoblock Europe. GDPR will be tricky to deal with. 
- What records will I need to keep permanently, w.r.t. US regulations? 

# tools

https://github.com/rgamble/libcsv C csv database tool. Store all customer data in a flat text file that I can easily read. Should be able to have a frontend that assigns a number to each customer, and tracks when the payments expire. One central database? Have a periodic emailer as a separate process for notifying when payments are due, etc. When a customer is 'deleted', move them to a db.deleted.csv file? (if US, otherwise if europe do something else?)

Frontend could be a pretty fast, mostly static html + php.  How to integrate paypal? How to integrate BTC?

paypal integration: use micropayments, eventually. Will require a separate paypal account, and a separate bank account. See: http://pressbin.com/tools/paypal_micropayments/, https://www.paypal.com/us/smarthelp/article/what-are-micropayments-faq664, https://www.paypal-community.com/t5/Merchant-services-Archive/What-is-the-minimum-price-I-can-sell-a-product-for-and-accept/td-p/401060#. I might not actually need a separate account: https://www.paypal.com/us/webapps/mpp/ua/digital-goods-micropayments-agreement.
