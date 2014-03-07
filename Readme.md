
# stripe-charges

  Query Stripe charges to get a time based overview of how much you're making.

## Example

Query charges by their `created` date:

```js
var query = require('stripe-charges')('stripe-key')

query(new Date('1/15/2014'), new Date('1/24/2014'), function (err, charges) {
  console.log('Made $' + charges.total() + ' in January!');
});
```

And the `charges` object lets you query information about this charge cohort.

#### Number of Charges

You can query the total amount of charges returned:

```js
charges.count();
```

or filter further inside the cohort by the charges' `created` date:

```js
charges.count(new Date('1/15/2014'), new Date('1/24/2014'));
```

#### Charges List

```js
charges.list()
```
```
[
  {
    amount: 2900,
    customer: 'cus_2983jd92d2d',
    ..
  }
}
]
```
or filter further by the charges' `created` date:

```js
charges.list(new Date('1/15/2014'), new Date('1/24/2014'));
```

or get all the `refunded` charges:

```js
charges.refunded(true).count();
```

#### Total Amount

You can get the total amount from the charges charges:

```js
charges.paid(true).refunded(false).total()
```

## License

MIT