---
layout: post
title: "How to convert JSON to VCard in JavaScript."
description: " "
date: 2023-09-24
tags: [JSONtoVCard]
comments: true
share: true
---

In this blog post, we will explore how to convert a JSON object to a VCard format using JavaScript. VCard is a standard format for electronic business cards and is widely used for sharing contact information.

To get started, we'll assume you have a JSON object containing contact information in the following format:

```javascript
const contact = {
  firstName: "John",
  lastName: "Doe",
  email: "john.doe@example.com",
  phone: "+1234567890",
  address: {
    street: "123 Main St",
    city: "Anytown",
    state: "CA",
    zip: "12345",
    country: "USA"
  }
};
```

To convert this JSON object to VCard, we can define a function that generates the VCard string:

```javascript
function jsonToVCard(contact) {
  const vcard = `BEGIN:VCARD
VERSION:3.0
FN:${contact.firstName} ${contact.lastName}
EMAIL:${contact.email}
TEL:${contact.phone}
ADR;TYPE=HOME;LABEL="${contact.address.street}, ${contact.address.city}, ${contact.address.state} ${contact.address.zip}, ${contact.address.country}"
END:VCARD`;

  return vcard;
}
```

In the `jsonToVCard` function, we concatenate the contact information into a VCard format using string interpolation.

To convert our JSON object to VCard, we can simply call the `jsonToVCard` function and pass in the `contact` object:

```javascript
const vcardString = jsonToVCard(contact);
console.log(vcardString);
```

This will output the following VCard string:

```
BEGIN:VCARD
VERSION:3.0
FN:John Doe
EMAIL:john.doe@example.com
TEL:+1234567890
ADR;TYPE=HOME;LABEL="123 Main St, Anytown, CA 12345, USA"
END:VCARD
```

With this approach, you can easily convert a JSON object to a VCard format in JavaScript.

## Conclusion

In this blog post, we demonstrated how to convert a JSON object to a VCard format using JavaScript. By following the provided code examples, you can convert contact information stored in JSON to a VCard string for easy sharing and integration with various applications.

#JSONtoVCard #JavaScript