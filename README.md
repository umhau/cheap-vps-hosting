# cheap-vps-hosting
The code to make the cheap vps hosting idea come alive

# architecture

Rent a VPN, tunnel all traffic through that. Keep the IP address for myself. When I get big enough for a rack, put openbsd on something that can handle the traffic and use that as a firewall.

Hardware: 256GB SSD for VMs, RAID 1 2x3TB HDDS for backup. Simple & easy. 

## networking 

https://tunnelbroker.net/ You could use TunnelBroker.net on top to get IPv6 if they don’t offer it and your use case requires it.  Our free tunnel broker service enables you to reach the IPv6 Internet by tunneling over existing IPv4 connections from your IPv6 enabled host or router to one of our IPv6 routers. 

## website construction

https://stackoverflow.com/questions/3126072/what-are-the-best-php-input-sanitizing-functions Make sure the website is safe.

https://zfs.rent/ https://news.ycombinator.com/item?id=25148000 https://radious.co/philosophy.txt Awesome website that fits the same type of market with the same type of customers and uses the same sort of aesthetics I imagined, but better executed than I would have done. Also their philosophy is to be admired and emulated.

### payment processing: paypal

https://wpforms.com/docs/how-to-test-paypal-payments-before-accepting-real-payments/ Paypal testing. 

paypal integration: use micropayments, eventually. Will require a separate paypal account, and a separate bank account. See: http://pressbin.com/tools/paypal_micropayments/, https://www.paypal.com/us/smarthelp/article/what-are-micropayments-faq664, https://www.paypal-community.com/t5/Merchant-services-Archive/What-is-the-minimum-price-I-can-sell-a-product-for-and-accept/td-p/401060#. I might not actually need a separate account: https://www.paypal.com/us/webapps/mpp/ua/digital-goods-micropayments-agreement.

## backend construction

https://git.sr.ht/~sircmpwn/himitsu safe way to store secret info - alternative to the .csv file

https://support.citrix.com/article/CTX117960 How to cap CPU execution cycles per-vm. Be aware of limitations?

# notes

- Don't forget to geoblock Europe. GDPR will be tricky to deal with. 
- What records will I need to keep permanently, w.r.t. US regulations? 

# tools

https://github.com/rgamble/libcsv C csv database tool. Store all customer data in a flat text file that I can easily read. Should be able to have a frontend that assigns a number to each customer, and tracks when the payments expire. One central database? Have a periodic emailer as a separate process for notifying when payments are due, etc. When a customer is 'deleted', move them to a db.deleted.csv file? (if US, otherwise if europe do something else?)

https://libguestfs.org/ libguestfs is a set of tools for accessing and modifying virtual machine (VM) disk images. You can use this for viewing and editing files inside guests, scripting changes to VMs, monitoring disk used/free statistics, creating guests, P2V, V2V, performing backups, cloning VMs, building VMs, formatting disks, resizing disks, and much more. 
Frontend could be a pretty fast, mostly static html + php.  

Note that BTC fees will drown out the actual profit. Charge by the year for BTC rates. Or find a different coin that works at small scales?

## host platform

OpenBSD + vmm? It would make life so much easier, if it worked - and it might be mature enough now? https://www.reddit.com/r/openbsd/comments/7qdsya/vmm4_production_use_and_performance/.  VCPUs aren't tied to a single processor, so I can set up more VMs than there are cores on the system. I can't control the speed of the cores, but I can let them scale down when the usage is high. Could work - but Xen would give me fancy dashboards.

## compliance

https://www.lowendtalk.com/discussion/164857/as-a-provider-what-tool-do-you-use-to-catch-a-vps-doing-stuff-not-allowed-in-your-tos See here for a discussion on how to deal with misbehaving VPS guests. Summary: I think I can stick with just responding to external takedown-type emails.

