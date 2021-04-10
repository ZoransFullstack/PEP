## Etebase
### The Need for End-to-End Encryption

It seems that with every week that goes by there's news of another huge company's website being breached. This is followed often by a vague statement from said company saying something along the lines of they are "looking into the matter"[^1]. If they release any other information after that, they might spend one or two sentences discussing the information that was accessed but spend a lot more time making assurances that they "took immediate action"[^2] and that the breach will be under "continued investigation"[^2]

It's usually not until security researchers start poking around that the scope of the breach is known. Often, it's found that the records that were accessed number in the millions and contain sensitive information such as login credentials, birth dates, credit cards, social security numbers, etc. And it's not long before these database dumps show up on the dark web for sale to the highest bidder and the genie is out of the bottle for good.

While most people affected by these breaches may only see a fraudulent charge on a credit card which is quickly taken care of by their credit company, unfortunately many breaches contain all the information needed for someone's identity to be stolen and used for much more damaging purposes. For example, in 2018 36% of identify theft claims reported to the Federal Trade Commission were classified as being related to employment/tax fraud, bank fraud, and loan/lease fraud.[^3] These types of identify fraud are much more difficult to resolve and it can sometimes take victims years of fighting to rectify.

Sadly, these types of fraud are likely to continue to increase largely because the companies who were trusted with this information in the first place rarely face any substantial consequences. One of the biggest examples of this can be seen in the Equifax breach of 2017 where the records of over 147 million people were stolen. 
As a result of a settlement with the FTC, Equifax ultimately only had to pay $125 to each victim but this was capped at $31 million meaning only .2 percent of the people affected were able to obtain this cash settlement. Equifax itself had to pay a fine which amounted to 2% of it's yearly revenue but faced no other legal repercussions. [^4]

### An "easy" fix

Databases will continue to be compromised as shown above and our personal information will most likely accessed by unauthorized individuals/parties which leads to the question, what more can companies, or us as developers, do to protect user data? The answer is implementing end-to-end encryption.

In a very high-level explanation, when end-to-end encryption is used data is encrypted on the client-side, before it gets sent to the server. Similarly, it is also only decrypted on the client side as well. This means that the owner of the server where your data is stored is at not able to read your data, nor could it be read if it were somehow intercepted in transit.

Now normally, end-to-end encryption is hard to implement, which is why you won't find it often in a lot of apps. That is, until a company Etesync came along and released an SDK called "Etebase" that it says "makes it easy to build end-to-end encrypted applications by taking care of the encryption and its related challenges."[^5]

Is this really as easy to implement as they say? Well, in this series of articles we're going to walk through the process of implementing Etebase in a simple app, starting with creating a user.

### Create a new React App

To create the foundation for our app quickly, let's leverage the "create-react-app" command that will give us everything we need by running the following command:

```javascript
npx create-react-app etebase-signup && cd etebase-signup
```

If you run `npm run start` you should see your default browser open and inside that browser, the react logo. This is the default behavior so let's make some changes.

Go to App.js and replace it with the following code which will render a very basic sign-up form with the functionality we need to capture the input:

```javascript
import React, { useState } from 'react';

function App() {
  const serverUrl = 'Your URL goes here';
  const [userData, setUserData] = useState({
	username: '',
	password: '',
  });

  async function Submit(evt) {
	evt.preventDefault();
	const formData = {
	  username: userData.username,
	  password: userData.password,
    };
	
	setUserData({
	  username: '',
	  password: '',
	  confirmPassword: '',
	});
  }

  const handleChange = (evt) => {
	setUserData({ ...userData, [evt.target.name]: evt.target.value });
  };

  return (
	<form onSubmit={Submit}>
	  <input
		type='email'
		name='email'
		value={userData.email}
		placeholder='Email'
		onChange={handleChange}
	  ></input>
	  <br />
	  <input
		type='username'
		name='username'
		value={userData.username}
		placeholder='Username'
		onChange={handleChange}
	  ></input>
	  <br />
	  <input
		type='password'
		name='password'
		value={userData.password}
		placeholder='Password'
		onChange={handleChange}
	  ></input>
	  <br />
	  <button type='submit'>Register</button>
	</form>
  );
}
  
export default App;
```

Now that we have everything we need, we can move forward with installing Etebase, creating a server, and lastly, signing up a user

### Install Etebase

First, let's get Etebase installed so in your terminal run the following command:

``` javascript
npm install etebase node-fetch
```

After this is done, be sure to import etebase at the top of App.js like so:

``` javascript
import * as Etebase from 'etebase'
```

### Sign Up For an Etebase Developer Account
Next we're going to need sign up for a developer account with Etebase and get a server URL. Since they are still in beta, they are offering this for so head on over to the below link to create the account:

https://dashboard.etebase.com/accounts/signup/

Once you've signed up and logged in, you should be given a server URL that you can use for testing. Copy this and paste it into App.js so that it is assigned to the serverUrl variable.

### Create a User

Next, let's add the few lines of code we need in order to register a user right before we clear the inputs. We'll also include an alert to confirm the user has been registered:

``` javascript
	const eteBaseUser = await Etebase.Account.signup(
	  {
		username: formData.username,
		email: formData.email,
	  },
	  formData.password,
	  serverUrl
	);
	alert(`Your user has been created!`)
	setData({
```

This should be all we need to add a user. Enter a username, email and password, press the Submit button, and you should see an alert pop-up confirming that the user has been created.

You can then navigate to your dashboard in Etebase, click on "Manger Users" in the User Management section and you should see the user created.

### Conclusion
As their docs say, registering a user is very straight-forward. In the next post, we're going to take it a step further and actually send some data to the server with this new user and then retrieve it and display it in our browser.

See you then!

[^1]: https://www.msn.com/en-us/money/companies/kroger-looking-into-data-breach-that-impacted-pharmacy-customers/ar-BB1dSypL
[^2]: https://www.techradar.com/news/sita-data-breach-affects-millions-of-airline-passengers
[^3]: https://bloom.co/blog/ultimate-guide-to-data-breaches-and-identity-theft/
[^4]: https://arstechnica.com/tech-policy/2020/05/banks-get-their-slice-of-equifax-settlement-individuals-still-waiting/?comments=1
[^5]: https://www.etebase.com/
