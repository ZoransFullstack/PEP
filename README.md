## Etebase
### The Need for End-to-End Encryption

It seems that with every week that goes by there's news of another huge company's website being breached. This is followed often by a vague statement from said company saying something along the lines of they are "looking into the matter"[^1]. If they release any other information after that, they might spend one or two sentences discussing the information that was accessed but spend a lot more time making assurances that they "took immediate action"[^2] and that the breach will be under "continued investigation"[^2]

It's usually not until security researchers start poking around that the scope of the breach is known. Often, it's found that the records that were accessed number in the millions and contain sensitive information such as login credentials, birth dates, credit cards, social security numbers, etc. And it's not long before these database dumps show up on the dark web for sale to the highest bidder and the genie is out of the bottle for good.

While most people affected by these breaches may only see a fraudulent charge on a credit card which is quickly taken care of by their credit company, unfortunately many breaches contain all the information needed for someone's identity to be stolen and used for much more damaging purposes. For example, in 2018 36% of identify theft claims reported to the Federal Trade Commission were classified as being related to employment/tax fraud, bank fraud, and loan/lease fraud.[^3] These types of identify fraud are much more difficult to resolve and it can sometimes take victims years of fighting to rectify.

Sadly, these types of fraud are likely to continue to increase largely because the companies who were trusted with this information in the first place rarely face any substantial consequences. One of the biggest examples of this can be seen in the Equifax breach of 2017 where the records of over 147 million people were stolen. 
As a result of a settlement with the FTC, Equifax ultimately only had to pay $125 to each victim but this was capped at $31 million meaning only .2 percent of the people affected were able to obtain this cash settlement. Equifax itself had to pay a fine which amounted to 2% of it's yearly revenue but faced no other legal repercussions. [^4]

(Discuss the issue of securing data when it's un-encrypted)

(Explain what end to end encryption is)

(Discuss how end-to-end encryption avoids almost everything about including 2FA)

### Etebase - Easy End-to-End Encryption for your App

(Discuss what is and what it does)

(Discuss how while it's easy to get running, you have to learn how to work with collections)

### Create a new React App

(Discuss how to create a react app using NPX and how to get it ready for Etebase)

### Install Etebase

First, let's get Etebase installed. Since we're going to be running this in Node, in your terminal run the following command:

``` javascript
npm install etebase node-fetch
```

(Show how to get a free server)

(Show how to connect the server)

(Show how to create a user)

``` javascript
// serverUrl can be obtained from the dashboard (or omitted for default)
const etebase = await Etebase.Account.signup({
  username: "username",
  email: "email"
}, "password", serverUrl);

```

(Show how to confirm a user has been created)

(Show how to save some data to the server)

(Show how to retrieve and show data from the server)

### Conclusion
(Talk about the benefits of using end to end-to-end encryption and also the downsides )

[^1]: https://www.msn.com/en-us/money/companies/kroger-looking-into-data-breach-that-impacted-pharmacy-customers/ar-BB1dSypL
[^2]: https://www.techradar.com/news/sita-data-breach-affects-millions-of-airline-passengers
[^3]: https://bloom.co/blog/ultimate-guide-to-data-breaches-and-identity-theft/
[^4]: https://arstechnica.com/tech-policy/2020/05/banks-get-their-slice-of-equifax-settlement-individuals-still-waiting/?comments=1
