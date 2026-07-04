# Subscriptions

## Overview

### Available Operations

* [create_subscription](#create_subscription) - Create subscription
* [add_subscription_addon](#add_subscription_addon) - Add addon to subscription
* [remove_subscription_addon](#remove_subscription_addon) - Remove addon from subscription
* [query_subscription_line_items](#query_subscription_line_items) - Search subscription line items
* [update_subscription_line_item](#update_subscription_line_item) - Update subscription line item
* [delete_subscription_line_item](#delete_subscription_line_item) - Delete subscription line item
* [query_subscription](#query_subscription) - Query subscriptions
* [get_subscription_usage](#get_subscription_usage) - Get usage by subscription
* [get_subscription](#get_subscription) - Get subscription
* [update_subscription](#update_subscription) - Update subscription
* [activate_subscription](#activate_subscription) - Activate draft subscription
* [get_subscription_addon_associations](#get_subscription_addon_associations) - Get active addon associations
* [cancel_subscription](#cancel_subscription) - Cancel subscription
* [execute_subscription_change](#execute_subscription_change) - Execute subscription plan change
* [preview_subscription_change](#preview_subscription_change) - Preview subscription plan change
* [get_subscription_entitlements](#get_subscription_entitlements) - Get subscription entitlements
* [get_subscription_upcoming_grants](#get_subscription_upcoming_grants) - Get upcoming credit grant applications
* [create_subscription_line_item](#create_subscription_line_item) - Create subscription line item
* [execute_subscription_modify](#execute_subscription_modify) - Execute subscription modification
* [preview_subscription_modify](#preview_subscription_modify) - Preview subscription modification
* [get_subscription_v2](#get_subscription_v2) - Get subscription (V2)
* [list_all_subscription_schedules](#list_all_subscription_schedules) - List all subscription schedules
* [get_subscription_schedule](#get_subscription_schedule) - Get subscription schedule
* [cancel_subscription_schedule](#cancel_subscription_schedule) - Cancel subscription schedule
* [list_subscription_schedules](#list_subscription_schedules) - List subscription schedules

## create_subscription

Use when onboarding a customer to a plan or starting a new subscription. Ideal for draft subscriptions (activate later) or active from start.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSubscription" method="post" path="/subscriptions" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.create_subscription(billing_period="ONETIME", currency="Kwacha", plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `billing_period`                                                                                                                                                                                                                                                                                                                                                                                                                | [models.BillingPeriod](../../models/billingperiod.md)                                                                                                                                                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `currency`                                                                                                                                                                                                                                                                                                                                                                                                                      | *str*                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `plan_id`                                                                                                                                                                                                                                                                                                                                                                                                                       | *str*                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `addons`                                                                                                                                                                                                                                                                                                                                                                                                                        | List[[models.AddAddonToSubscriptionRequest](../../models/addaddontosubscriptionrequest.md)]                                                                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Addons represents addons to be added to the subscription during creation                                                                                                                                                                                                                                                                                                                                                        |
| `auto_invoice_threshold`                                                                                                                                                                                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | AutoInvoiceThreshold is the usage amount (in subscription currency) that triggers<br/>an intermediate invoice mid-period. Set once at creation; cannot be changed later.<br/>Allowed only when the subscription resolves to type standalone (no parent hierarchy rows).<br/>Plan line items must be usage-based only (no fixed or other non-usage plan prices).<br/>Nil means auto invoice threshold billing is disabled for this subscription. |
| `billing_anchor`                                                                                                                                                                                                                                                                                                                                                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | BillingAnchor overrides the derived billing anchor when billing_cycle is anniversary.<br/>For monthly billing, the day-of-month (and time-of-day) define cycle boundaries: if start_date<br/>is before that day in the month, the first billing period ends on the next occurrence of that<br/>day in the same month (a shorter first period); subsequent periods follow the usual interval.                                    |
| `billing_cycle`                                                                                                                                                                                                                                                                                                                                                                                                                 | [Optional[models.BillingCycle]](../../models/billingcycle.md)                                                                                                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `billing_period_count`                                                                                                                                                                                                                                                                                                                                                                                                          | *Optional[int]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `collection_method`                                                                                                                                                                                                                                                                                                                                                                                                             | [Optional[models.CollectionMethod]](../../models/collectionmethod.md)                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `commitment_amount`                                                                                                                                                                                                                                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | CommitmentAmount is the minimum amount a customer commits to paying for a billing period                                                                                                                                                                                                                                                                                                                                        |
| `commitment_duration`                                                                                                                                                                                                                                                                                                                                                                                                           | [Optional[models.BillingPeriod]](../../models/billingperiod.md)                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `coupons`                                                                                                                                                                                                                                                                                                                                                                                                                       | List[*str*]                                                                                                                                                                                                                                                                                                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Deprecated: use SubscriptionCoupons instead.                                                                                                                                                                                                                                                                                                                                                                                    |
| `credit_grants`                                                                                                                                                                                                                                                                                                                                                                                                                 | List[[models.CreateCreditGrantRequest](../../models/createcreditgrantrequest.md)]                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Credit grants to be applied when subscription is created                                                                                                                                                                                                                                                                                                                                                                        |
| `customer_id`                                                                                                                                                                                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | customer_id is the tirdad customer id<br/>and it is prioritized over external_customer_id in case both are provided.                                                                                                                                                                                                                                                                                                         |
| `enable_true_up`                                                                                                                                                                                                                                                                                                                                                                                                                | *Optional[bool]*                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Enable Commitment True Up Fee                                                                                                                                                                                                                                                                                                                                                                                                   |
| `end_date`                                                                                                                                                                                                                                                                                                                                                                                                                      | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `external_customer_id`                                                                                                                                                                                                                                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | external_customer_id is the customer id in your DB<br/>and must be same as what you provided as external_id while creating the customer in tirdad.                                                                                                                                                                                                                                                                           |
| `gateway_payment_method_id`                                                                                                                                                                                                                                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `inheritance`                                                                                                                                                                                                                                                                                                                                                                                                                   | [Optional[models.SubscriptionInheritanceConfig]](../../models/subscriptioninheritanceconfig.md)                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `line_item_commitments`                                                                                                                                                                                                                                                                                                                                                                                                         | Dict[str, [models.LineItemCommitmentConfig](../../models/lineitemcommitmentconfig.md)]                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | LineItemCommitments allows setting commitment configuration per line item (keyed by price_id)                                                                                                                                                                                                                                                                                                                                   |
| `line_item_coupons`                                                                                                                                                                                                                                                                                                                                                                                                             | Dict[str, List[*str*]]                                                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Deprecated: use SubscriptionCoupons instead.                                                                                                                                                                                                                                                                                                                                                                                    |
| `line_items`                                                                                                                                                                                                                                                                                                                                                                                                                    | List[[models.CreateSubscriptionLineItemRequest](../../models/createsubscriptionlineitemrequest.md)]                                                                                                                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | LineItems are extra line items to add at creation (each with price_id or price), in addition to plan prices                                                                                                                                                                                                                                                                                                                     |
| `lookup_key`                                                                                                                                                                                                                                                                                                                                                                                                                    | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `metadata`                                                                                                                                                                                                                                                                                                                                                                                                                      | Dict[str, *str*]                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `overage_factor`                                                                                                                                                                                                                                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | OverageFactor is a multiplier applied to usage beyond the commitment amount                                                                                                                                                                                                                                                                                                                                                     |
| `override_entitlements`                                                                                                                                                                                                                                                                                                                                                                                                         | List[[models.OverrideEntitlementRequest](../../models/overrideentitlementrequest.md)]                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | OverrideEntitlements allows customizing specific entitlements for this subscription                                                                                                                                                                                                                                                                                                                                             |
| `override_line_items`                                                                                                                                                                                                                                                                                                                                                                                                           | List[[models.OverrideLineItemRequest](../../models/overridelineitemrequest.md)]                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | OverrideLineItems allows customizing specific prices for this subscription                                                                                                                                                                                                                                                                                                                                                      |
| `payment_behavior`                                                                                                                                                                                                                                                                                                                                                                                                              | [Optional[models.PaymentBehavior]](../../models/paymentbehavior.md)                                                                                                                                                                                                                                                                                                                                                             | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `payment_terms`                                                                                                                                                                                                                                                                                                                                                                                                                 | [Optional[models.PaymentTerms]](../../models/paymentterms.md)                                                                                                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `phases`                                                                                                                                                                                                                                                                                                                                                                                                                        | List[[models.SubscriptionPhaseCreateRequest](../../models/subscriptionphasecreaterequest.md)]                                                                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Phases represents subscription phases to be created with the subscription                                                                                                                                                                                                                                                                                                                                                       |
| `proration_behavior`                                                                                                                                                                                                                                                                                                                                                                                                            | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md)                                                                                                                                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `start_date`                                                                                                                                                                                                                                                                                                                                                                                                                    | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `subscription_coupons`                                                                                                                                                                                                                                                                                                                                                                                                          | List[[models.SubscriptionCouponInput](../../models/subscriptioncouponinput.md)]                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | SubscriptionCoupons is the preferred way to attach coupons at creation.<br/>Accepts coupon_code; optionally targets a line item via price_id.                                                                                                                                                                                                                                                                                   |
| `subscription_status`                                                                                                                                                                                                                                                                                                                                                                                                           | [Optional[models.SubscriptionStatus]](../../models/subscriptionstatus.md)                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `tax_rate_overrides`                                                                                                                                                                                                                                                                                                                                                                                                            | List[[models.TaxRateOverride](../../models/taxrateoverride.md)]                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | tax_rate_overrides is the tax rate overrides	to be applied to the subscription                                                                                                                                                                                                                                                                                                                                                  |
| `timezone`                                                                                                                                                                                                                                                                                                                                                                                                                      | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Timezone of the customer.<br/>If not set, the default value is UTC.                                                                                                                                                                                                                                                                                                                                                             |
| `trial_period_days`                                                                                                                                                                                                                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | TrialPeriodDays: nil = inherit trial length from plan recurring-fixed prices (must be uniform).<br/>0 = explicitly no trial (overrides catalog). >0 = override duration in days.                                                                                                                                                                                                                                                |
| `retries`                                                                                                                                                                                                                                                                                                                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                                                                             |

### Response

**[models.SubscriptionResponse](../../models/subscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## add_subscription_addon

Use when adding an optional product or add-on to an existing subscription (e.g. extra storage or support tier).

### Example Usage

<!-- UsageSnippet language="python" operationID="addSubscriptionAddon" method="post" path="/subscriptions/addon" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.add_subscription_addon(addon_id="<id>", subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `addon_id`                                                                                          | *str*                                                                                               | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `subscription_id`                                                                                   | *str*                                                                                               | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `cadence`                                                                                           | [Optional[models.AddonCadence]](../../models/addoncadence.md)                                       | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `line_item_commitments`                                                                             | Dict[str, [models.LineItemCommitmentConfig](../../models/lineitemcommitmentconfig.md)]              | :heavy_minus_sign:                                                                                  | LineItemCommitments allows setting commitment configuration per addon line item (keyed by price_id) |
| `metadata`                                                                                          | Dict[str, *Any*]                                                                                    | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `proration_behavior`                                                                                | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md)                             | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `start_date`                                                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `retries`                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                    | :heavy_minus_sign:                                                                                  | Configuration to override the default retry behavior of the client.                                 |

### Response

**[models.AddonAssociationResponse](../../models/addonassociationresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## remove_subscription_addon

Use when removing an add-on from a subscription (e.g. downgrade or opt-out).

### Example Usage

<!-- UsageSnippet language="python" operationID="removeSubscriptionAddon" method="delete" path="/subscriptions/addon" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.remove_subscription_addon(addon_association_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                          | Type                                                                                                                                                                                                                                                                                               | Required                                                                                                                                                                                                                                                                                           | Description                                                                                                                                                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `addon_association_id`                                                                                                                                                                                                                                                                             | *str*                                                                                                                                                                                                                                                                                              | :heavy_check_mark:                                                                                                                                                                                                                                                                                 | N/A                                                                                                                                                                                                                                                                                                |
| `effective_date`                                                                                                                                                                                                                                                                                   | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                 | EffectiveDate is the date the cancellation takes effect.<br/>When nil the addon is cancelled at the end of the current period.<br/>When provided it must fall within [CurrentPeriodStart, CurrentPeriodEnd]; mid-period<br/>values combined with create_prorations will issue a wallet credit for unused time. |
| `proration_behavior`                                                                                                                                                                                                                                                                               | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md)                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                 | N/A                                                                                                                                                                                                                                                                                                |
| `reason`                                                                                                                                                                                                                                                                                           | *Optional[str]*                                                                                                                                                                                                                                                                                    | :heavy_minus_sign:                                                                                                                                                                                                                                                                                 | N/A                                                                                                                                                                                                                                                                                                |
| `retries`                                                                                                                                                                                                                                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                 | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                |

### Response

**[models.SuccessResponse](../../models/successresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_subscription_line_items

List subscription line items with a JSON filter (subscription, customer, price, pagination, expand=prices, etc.).

### Example Usage

<!-- UsageSnippet language="python" operationID="querySubscriptionLineItems" method="post" path="/subscriptions/lineitems/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.query_subscription_line_items(active_filter=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `active_filter`                                                                                     | *Optional[bool]*                                                                                    | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `addon_association_ids`                                                                             | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `billing_periods`                                                                                   | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `currencies`                                                                                        | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `current_period_start`                                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `customer_ids`                                                                                      | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `end_time`                                                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `entity_ids`                                                                                        | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `entity_type`                                                                                       | [Optional[models.SubscriptionLineItemEntityType]](../../models/subscriptionlineitementitytype.md)   | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `expand`                                                                                            | *Optional[str]*                                                                                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `filters`                                                                                           | List[[models.FilterCondition](../../models/filtercondition.md)]                                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `limit`                                                                                             | *Optional[int]*                                                                                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `meter_ids`                                                                                         | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `offset`                                                                                            | *Optional[int]*                                                                                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `order`                                                                                             | [Optional[models.SubscriptionLineItemFilterOrder]](../../models/subscriptionlineitemfilterorder.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `price_ids`                                                                                         | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `sort`                                                                                              | List[[models.SortCondition](../../models/sortcondition.md)]                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `start_time`                                                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `status`                                                                                            | [Optional[models.Status]](../../models/status.md)                                                   | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `subscription_ids`                                                                                  | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `subscription_line_item_ids`                                                                        | List[*str*]                                                                                         | :heavy_minus_sign:                                                                                  | Specific filters                                                                                    |
| `retries`                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                    | :heavy_minus_sign:                                                                                  | Configuration to override the default retry behavior of the client.                                 |

### Response

**[models.ListSubscriptionLineItemsResponse](../../models/listsubscriptionlineitemsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_subscription_line_item

Use when changing a subscription line item (e.g. quantity or price). Implemented by ending the current line and creating a new one for clean billing.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSubscriptionLineItem" method="put" path="/subscriptions/lineitems/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.update_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `id`                                                                                 | *str*                                                                                | :heavy_check_mark:                                                                   | Line Item ID                                                                         |
| `amount`                                                                             | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | Amount is the new price amount that overrides the original price                     |
| `billing_model`                                                                      | [Optional[models.BillingModel]](../../models/billingmodel.md)                        | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_amount`                                                                  | *Optional[float]*                                                                    | :heavy_minus_sign:                                                                   | Commitment fields                                                                    |
| `commitment_duration`                                                                | [Optional[models.BillingPeriod]](../../models/billingperiod.md)                      | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_overage_factor`                                                          | *Optional[float]*                                                                    | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_quantity`                                                                | *Optional[float]*                                                                    | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_time_buckets`                                                            | List[[models.CommitmentBucketRequest](../../models/commitmentbucketrequest.md)]      | :heavy_minus_sign:                                                                   | Pointer so an explicit empty array can clear existing buckets (omission keeps them). |
| `commitment_true_up_enabled`                                                         | *Optional[bool]*                                                                     | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_type`                                                                    | [Optional[models.CommitmentType]](../../models/commitmenttype.md)                    | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `commitment_windowed`                                                                | *Optional[bool]*                                                                     | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `effective_from`                                                                     | *Optional[str]*                                                                      | :heavy_minus_sign:                                                                   | EffectiveFrom for the existing line item (if not provided, defaults to now)          |
| `metadata`                                                                           | Dict[str, *str*]                                                                     | :heavy_minus_sign:                                                                   | Metadata for the new line item                                                       |
| `tier_mode`                                                                          | [Optional[models.BillingTier]](../../models/billingtier.md)                          | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `tiers`                                                                              | List[[models.CreatePriceTier](../../models/createpricetier.md)]                      | :heavy_minus_sign:                                                                   | Tiers determines the pricing tiers for this line item                                |
| `transform_quantity`                                                                 | [Optional[models.PriceTransformQuantity]](../../models/pricetransformquantity.md)    | :heavy_minus_sign:                                                                   | N/A                                                                                  |
| `retries`                                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                     | :heavy_minus_sign:                                                                   | Configuration to override the default retry behavior of the client.                  |

### Response

**[models.SubscriptionLineItemResponse](../../models/subscriptionlineitemresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## delete_subscription_line_item

Use when removing a charge or seat from a subscription (e.g. downgrade). Line item ends; retained for history but no longer billed.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteSubscriptionLineItem" method="delete" path="/subscriptions/lineitems/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.delete_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `id`                                                                    | *str*                                                                   | :heavy_check_mark:                                                      | Line Item ID                                                            |
| `effective_from`                                                        | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `proration_behavior`                                                    | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md) | :heavy_minus_sign:                                                      | N/A                                                                     |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.SubscriptionLineItemResponse](../../models/subscriptionlineitemresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## query_subscription

Use when listing or searching subscriptions (e.g. admin view or customer subscription list). Returns a paginated list; supports filtering by customer, plan, status.

### Example Usage

<!-- UsageSnippet language="python" operationID="querySubscription" method="post" path="/subscriptions/search" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.query_subscription()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                  | Type                                                                                                                                                                                                                                                                                                       | Required                                                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `active_at`                                                                                                                                                                                                                                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | ActiveAt filters subscriptions that are active at the given time                                                                                                                                                                                                                                           |
| `billing_cadence`                                                                                                                                                                                                                                                                                          | List[[models.BillingCadence](../../models/billingcadence.md)]                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | BillingCadence filters by billing cadence                                                                                                                                                                                                                                                                  |
| `billing_period`                                                                                                                                                                                                                                                                                           | List[[models.BillingPeriod](../../models/billingperiod.md)]                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | BillingPeriod filters by billing period                                                                                                                                                                                                                                                                    |
| `customer_id`                                                                                                                                                                                                                                                                                              | *Optional[str]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | CustomerID filters by customer ID                                                                                                                                                                                                                                                                          |
| `customer_ids`                                                                                                                                                                                                                                                                                             | List[*str*]                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | CustomerIDs filters by customer IDs                                                                                                                                                                                                                                                                        |
| `effective_date_for_update`                                                                                                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | EffectiveDateForUpdate selects subscriptions that need a billing-period pass on or before this time:<br/>current_period_end <= date OR (cancel_at IS NOT NULL AND cancel_at <= date).<br/>When nil, period/cancel cutoff logic is not applied by this field (see TimeRangeFilter for legacy period-end filtering). |
| `end_time`                                                                                                                                                                                                                                                                                                 | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `expand`                                                                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `external_customer_id`                                                                                                                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | ExternalCustomerID filters by external customer ID                                                                                                                                                                                                                                                         |
| `filters`                                                                                                                                                                                                                                                                                                  | List[[models.FilterCondition](../../models/filtercondition.md)]                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `invoicing_customer_ids`                                                                                                                                                                                                                                                                                   | List[*str*]                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | InvoicingCustomerIDs filters by invoicing customer ID                                                                                                                                                                                                                                                      |
| `limit`                                                                                                                                                                                                                                                                                                    | *Optional[int]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `offset`                                                                                                                                                                                                                                                                                                   | *Optional[int]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `order`                                                                                                                                                                                                                                                                                                    | [Optional[models.SubscriptionFilterOrder]](../../models/subscriptionfilterorder.md)                                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `parent_subscription_ids`                                                                                                                                                                                                                                                                                  | List[*str*]                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | ParentSubscriptionIDs filters by parent subscription IDs                                                                                                                                                                                                                                                   |
| `plan_id`                                                                                                                                                                                                                                                                                                  | *Optional[str]*                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | PlanID filters by plan ID                                                                                                                                                                                                                                                                                  |
| `sort`                                                                                                                                                                                                                                                                                                     | List[[models.SortCondition](../../models/sortcondition.md)]                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `start_time`                                                                                                                                                                                                                                                                                               | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `status`                                                                                                                                                                                                                                                                                                   | [Optional[models.Status]](../../models/status.md)                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `subscription_ids`                                                                                                                                                                                                                                                                                         | List[*str*]                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                        |
| `subscription_status`                                                                                                                                                                                                                                                                                      | List[[models.SubscriptionStatus](../../models/subscriptionstatus.md)]                                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | SubscriptionStatus filters by subscription status                                                                                                                                                                                                                                                          |
| `subscription_type`                                                                                                                                                                                                                                                                                        | List[[models.SubscriptionType](../../models/subscriptiontype.md)]                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | SubscriptionType filters by subscription type                                                                                                                                                                                                                                                              |
| `trial_end_due_lte`                                                                                                                                                                                                                                                                                        | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | TrialEndDueLTE, when set, restricts to subscriptions with trial_end not nil and trial_end <= trial_end_due_lte.<br/>Use with subscription_status trialing for trial-end cron processing.                                                                                                                   |
| `with_line_items`                                                                                                                                                                                                                                                                                          | *Optional[bool]*                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | WithLineItems includes line items in the response                                                                                                                                                                                                                                                          |
| `retries`                                                                                                                                                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                        |

### Response

**[models.ListSubscriptionsResponse](../../models/listsubscriptionsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_usage

Use when showing usage for a subscription (e.g. in a portal or for overage checks). Supports time range and filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionUsage" method="post" path="/subscriptions/usage" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_usage(subscription_id="123", end_time=parse_datetime("2024-03-20T00:00:00Z"), lifetime_usage=False, start_time=parse_datetime("2024-03-13T00:00:00Z"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          | Example                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `subscription_id`                                                    | *str*                                                                | :heavy_check_mark:                                                   | N/A                                                                  | 123                                                                  |
| `end_time`                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  | 2024-03-20T00:00:00Z                                                 |
| `lifetime_usage`                                                     | *Optional[bool]*                                                     | :heavy_minus_sign:                                                   | N/A                                                                  | false                                                                |
| `start_time`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | N/A                                                                  | 2024-03-13T00:00:00Z                                                 |
| `retries`                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)     | :heavy_minus_sign:                                                   | Configuration to override the default retry behavior of the client.  |                                                                      |

### Response

**[models.GetUsageBySubscriptionResponse](../../models/getusagebysubscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription

Use when you need to load a single subscription (e.g. for a billing portal or to check status).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscription" method="get" path="/subscriptions/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SubscriptionResponse](../../models/subscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## update_subscription

Use when changing subscription details (e.g. quantity, billing anchor, or parent). Supports partial update; send "" to clear parent_subscription_id.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSubscription" method="put" path="/subscriptions/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.update_subscription(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                    | *str*                                                                                                   | :heavy_check_mark:                                                                                      | Subscription ID                                                                                         |
| `cancel_at`                                                                                             | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                    | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `cancel_at_period_end`                                                                                  | *Optional[bool]*                                                                                        | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `parent_subscription_id`                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | ParentSubscriptionID sets or clears the parent subscription. Omit to leave unchanged; send "" to clear. |
| `status`                                                                                                | [Optional[models.SubscriptionStatus]](../../models/subscriptionstatus.md)                               | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |

### Response

**[models.SubscriptionResponse](../../models/subscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## activate_subscription

Use when turning a draft subscription live (e.g. after collecting payment or completing setup). Once activated, billing and entitlements apply.

### Example Usage

<!-- UsageSnippet language="python" operationID="activateSubscription" method="post" path="/subscriptions/{id}/activate" -->
```python
from tirdad_sdk import Tirdad
from tirdad_sdk.utils import parse_datetime


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.activate_subscription(id="<id>", start_date=parse_datetime("2026-02-04T05:02:31.632Z"))

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `id`                                                                  | *str*                                                                 | :heavy_check_mark:                                                    | Subscription ID                                                       |
| `start_date`                                                          | [date](https://docs.python.org/3/library/datetime.html#date-objects)  | :heavy_check_mark:                                                    | start_date is the new start date for the subscription when activating |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.SubscriptionResponse](../../models/subscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_addon_associations

Use when listing which add-ons are currently attached to a subscription (e.g. for display or editing).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionAddonAssociations" method="get" path="/subscriptions/{id}/addons/associations" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_addon_associations(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.AddonAssociationResponse]](../../models/.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## cancel_subscription

Use when a customer churns or downgrades. Supports immediate or end-of-period cancellation and proration. Ideal for self-serve or support-driven cancellations.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelSubscription" method="post" path="/subscriptions/{id}/cancel" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.cancel_subscription(id="<id>", cancellation_type="immediate")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                  | Type                                                                                                                                                                                                                                                                                                                                                                                                       | Required                                                                                                                                                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                                                                                                                                                                                                                       | *str*                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                         | Subscription ID                                                                                                                                                                                                                                                                                                                                                                                            |
| `cancellation_type`                                                                                                                                                                                                                                                                                                                                                                                        | [models.CancellationType](../../models/cancellationtype.md)                                                                                                                                                                                                                                                                                                                                                | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                        |
| `cancel_at`                                                                                                                                                                                                                                                                                                                                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                         | CancelAt is the exact date/time when the subscription should be cancelled.<br/>Required for cancellation_type "scheduled_date"; optional for "immediate" (past dates only — backdated cancellation).<br/>For "scheduled_date", accepts both future dates (deferred cancellation) and past dates (backdated cancellation).<br/>For "immediate", accepts past/current dates only; use "scheduled_date" for future dates. |
| `cancel_immediately_inovice_policy`                                                                                                                                                                                                                                                                                                                                                                        | [Optional[models.CancelImmediatelyInvoicePolicy]](../../models/cancelimmediatelyinvoicepolicy.md)                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                        |
| `proration_behavior`                                                                                                                                                                                                                                                                                                                                                                                       | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md)                                                                                                                                                                                                                                                                                                                                    | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                        |
| `reason`                                                                                                                                                                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                         | Reason for cancellation (for audit and business intelligence)                                                                                                                                                                                                                                                                                                                                              |
| `retries`                                                                                                                                                                                                                                                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                                                        |

### Response

**[models.CancelSubscriptionResponse](../../models/cancelsubscriptionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## execute_subscription_change

Use when applying a plan change (e.g. upgrade or downgrade). Executes proration and generates invoice or credit as needed.

### Example Usage

<!-- UsageSnippet language="python" operationID="executeSubscriptionChange" method="post" path="/subscriptions/{id}/change/execute" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.execute_subscription_change(id="<id>", billing_cadence="RECURRING", billing_cycle="anniversary", billing_period="ANNUAL", proration_behavior="none", target_plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `id`                                                                       | *str*                                                                      | :heavy_check_mark:                                                         | Subscription ID                                                            |
| `billing_cadence`                                                          | [models.BillingCadence](../../models/billingcadence.md)                    | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_cycle`                                                            | [models.BillingCycle](../../models/billingcycle.md)                        | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_period`                                                           | [models.BillingPeriod](../../models/billingperiod.md)                      | :heavy_check_mark:                                                         | N/A                                                                        |
| `proration_behavior`                                                       | [models.ProrationBehavior](../../models/prorationbehavior.md)              | :heavy_check_mark:                                                         | N/A                                                                        |
| `target_plan_id`                                                           | *str*                                                                      | :heavy_check_mark:                                                         | target_plan_id is the ID of the new plan to change to (required)           |
| `billing_period_count`                                                     | *Optional[int]*                                                            | :heavy_minus_sign:                                                         | billing_period_count is the billing period count for the new subscription  |
| `change_at`                                                                | [Optional[models.ScheduleType]](../../models/scheduletype.md)              | :heavy_minus_sign:                                                         | N/A                                                                        |
| `metadata`                                                                 | Dict[str, *str*]                                                           | :heavy_minus_sign:                                                         | metadata contains additional key-value pairs for storing extra information |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[models.SubscriptionChangeExecuteResponse](../../models/subscriptionchangeexecuteresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## preview_subscription_change

Use when showing a customer the cost of a plan change before they confirm (e.g. upgrade/downgrade preview with proration).

### Example Usage

<!-- UsageSnippet language="python" operationID="previewSubscriptionChange" method="post" path="/subscriptions/{id}/change/preview" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.preview_subscription_change(id="<id>", billing_cadence="RECURRING", billing_cycle="anniversary", billing_period="ONETIME", proration_behavior="none", target_plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `id`                                                                       | *str*                                                                      | :heavy_check_mark:                                                         | Subscription ID                                                            |
| `billing_cadence`                                                          | [models.BillingCadence](../../models/billingcadence.md)                    | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_cycle`                                                            | [models.BillingCycle](../../models/billingcycle.md)                        | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_period`                                                           | [models.BillingPeriod](../../models/billingperiod.md)                      | :heavy_check_mark:                                                         | N/A                                                                        |
| `proration_behavior`                                                       | [models.ProrationBehavior](../../models/prorationbehavior.md)              | :heavy_check_mark:                                                         | N/A                                                                        |
| `target_plan_id`                                                           | *str*                                                                      | :heavy_check_mark:                                                         | target_plan_id is the ID of the new plan to change to (required)           |
| `billing_period_count`                                                     | *Optional[int]*                                                            | :heavy_minus_sign:                                                         | billing_period_count is the billing period count for the new subscription  |
| `change_at`                                                                | [Optional[models.ScheduleType]](../../models/scheduletype.md)              | :heavy_minus_sign:                                                         | N/A                                                                        |
| `metadata`                                                                 | Dict[str, *str*]                                                           | :heavy_minus_sign:                                                         | metadata contains additional key-value pairs for storing extra information |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[models.SubscriptionChangePreviewResponse](../../models/subscriptionchangepreviewresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_entitlements

Use when checking what features or limits a subscription has (e.g. entitlement checks or feature gating). Optional feature_ids to filter.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionEntitlements" method="get" path="/subscriptions/{id}/entitlements" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `feature_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | Feature IDs to filter by                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SubscriptionEntitlementsResponse](../../models/subscriptionentitlementsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_upcoming_grants

Use when showing upcoming or pending credits for a subscription (e.g. in a portal or for forecasting).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionUpcomingGrants" method="get" path="/subscriptions/{id}/grants/upcoming" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_upcoming_grants(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListCreditGrantApplicationsResponse](../../models/listcreditgrantapplicationsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## create_subscription_line_item

Use when adding a new charge or seat to a subscription (e.g. extra seat or one-time add). Supports price_id or inline price.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSubscriptionLineItem" method="post" path="/subscriptions/{id}/lineitems" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.create_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                 | Type                                                                                                                      | Required                                                                                                                  | Description                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                      | *str*                                                                                                                     | :heavy_check_mark:                                                                                                        | Subscription ID                                                                                                           |
| `commitment_amount`                                                                                                       | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | Commitment fields                                                                                                         |
| `commitment_duration`                                                                                                     | [Optional[models.BillingPeriod]](../../models/billingperiod.md)                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_overage_factor`                                                                                               | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_quantity`                                                                                                     | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_time_buckets`                                                                                                 | List[[models.CommitmentBucketRequest](../../models/commitmentbucketrequest.md)]                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_true_up_enabled`                                                                                              | *Optional[bool]*                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_type`                                                                                                         | [Optional[models.CommitmentType]](../../models/commitmenttype.md)                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_windowed`                                                                                                     | *Optional[bool]*                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `display_name`                                                                                                            | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `end_date`                                                                                                                | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                      | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `metadata`                                                                                                                | Dict[str, *str*]                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `price`                                                                                                                   | [Optional[models.SubscriptionPriceCreateRequest]](../../models/subscriptionpricecreaterequest.md)                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `price_id`                                                                                                                | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | PriceID references an existing price (plan, addon, or subscription-scoped). Exactly one of price_id or price must be set. |
| `proration_behavior`                                                                                                      | [Optional[models.ProrationBehavior]](../../models/prorationbehavior.md)                                                   | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `quantity`                                                                                                                | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `start_date`                                                                                                              | [date](https://docs.python.org/3/library/datetime.html#date-objects)                                                      | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `subscription_phase_id`                                                                                                   | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `retries`                                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                          | :heavy_minus_sign:                                                                                                        | Configuration to override the default retry behavior of the client.                                                       |

### Response

**[models.SubscriptionLineItemResponse](../../models/subscriptionlineitemresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## execute_subscription_modify

Execute a mid-cycle subscription modification (inheritance, quantity change, grouped invoicing, trial end, coupon, or tax).

### Example Usage

<!-- UsageSnippet language="python" operationID="executeSubscriptionModify" method="post" path="/subscriptions/{id}/modify/execute" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.execute_subscription_modify(id="<id>", type_="inheritance")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `id`                                                                                                | *str*                                                                                               | :heavy_check_mark:                                                                                  | Subscription ID                                                                                     |
| `type`                                                                                              | [models.SubscriptionModifyType](../../models/subscriptionmodifytype.md)                             | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `coupon_params`                                                                                     | [Optional[models.SubModifyCouponParams]](../../models/submodifycouponparams.md)                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `grouped_invoicing_params`                                                                          | [Optional[models.SubModifyGroupedInvoicingParams]](../../models/submodifygroupedinvoicingparams.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `inheritance_params`                                                                                | [Optional[models.SubModifyInheritanceRequest]](../../models/submodifyinheritancerequest.md)         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `quantity_change_params`                                                                            | [Optional[models.SubModifyQuantityChangeRequest]](../../models/submodifyquantitychangerequest.md)   | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `tax_params`                                                                                        | [Optional[models.SubModifyTaxParams]](../../models/submodifytaxparams.md)                           | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `trial_end_params`                                                                                  | [Optional[models.SubModifyTrialEndRequest]](../../models/submodifytrialendrequest.md)               | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `retries`                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                    | :heavy_minus_sign:                                                                                  | Configuration to override the default retry behavior of the client.                                 |

### Response

**[models.SubscriptionModifyResponse](../../models/subscriptionmodifyresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## preview_subscription_modify

Preview the impact of a mid-cycle subscription modification (inheritance, quantity change, grouped invoicing, trial end, coupon, or tax) without committing changes.

### Example Usage

<!-- UsageSnippet language="python" operationID="previewSubscriptionModify" method="post" path="/subscriptions/{id}/modify/preview" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.preview_subscription_modify(id="<id>", type_="coupon")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `id`                                                                                                | *str*                                                                                               | :heavy_check_mark:                                                                                  | Subscription ID                                                                                     |
| `type`                                                                                              | [models.SubscriptionModifyType](../../models/subscriptionmodifytype.md)                             | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `coupon_params`                                                                                     | [Optional[models.SubModifyCouponParams]](../../models/submodifycouponparams.md)                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `grouped_invoicing_params`                                                                          | [Optional[models.SubModifyGroupedInvoicingParams]](../../models/submodifygroupedinvoicingparams.md) | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `inheritance_params`                                                                                | [Optional[models.SubModifyInheritanceRequest]](../../models/submodifyinheritancerequest.md)         | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `quantity_change_params`                                                                            | [Optional[models.SubModifyQuantityChangeRequest]](../../models/submodifyquantitychangerequest.md)   | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `tax_params`                                                                                        | [Optional[models.SubModifyTaxParams]](../../models/submodifytaxparams.md)                           | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `trial_end_params`                                                                                  | [Optional[models.SubModifyTrialEndRequest]](../../models/submodifytrialendrequest.md)               | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `retries`                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                    | :heavy_minus_sign:                                                                                  | Configuration to override the default retry behavior of the client.                                 |

### Response

**[models.SubscriptionModifyResponse](../../models/subscriptionmodifyresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400, 404                         | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_v2

Use when you need a subscription with related data (line items, prices, plan). Supports expand for detailed payloads without extra round-trips.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionV2" method="get" path="/subscriptions/{id}/v2" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_v2(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `id`                                                                                   | *str*                                                                                  | :heavy_check_mark:                                                                     | Subscription ID                                                                        |
| `expand`                                                                               | *Optional[str]*                                                                        | :heavy_minus_sign:                                                                     | Comma-separated list of fields to expand (e.g., 'subscription_line_items,prices,plan') |
| `retries`                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                       | :heavy_minus_sign:                                                                     | Configuration to override the default retry behavior of the client.                    |

### Response

**[models.SubscriptionResponseV2](../../models/subscriptionresponsev2.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.ErrorResponse      | 400                              | application/json                 |
| models.errors.ErrorResponse      | 500                              | application/json                 |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## list_all_subscription_schedules

Use when listing or searching scheduled changes across subscriptions (e.g. admin view). Returns schedules with optional filtering.

### Example Usage

<!-- UsageSnippet language="python" operationID="listAllSubscriptionSchedules" method="get" path="/v1/subscription-schedules" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.list_all_subscription_schedules()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `pending_only`                                                      | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Filter to pending schedules only                                    |
| `subscription_id`                                                   | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by subscription ID                                           |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Limit results                                                       |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Offset for pagination                                               |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetPendingSchedulesResponse](../../models/getpendingschedulesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## get_subscription_schedule

Use when you need to load a single scheduled change (e.g. to show when a plan change or renewal takes effect).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionSchedule" method="get" path="/v1/subscription-schedules/{id}" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.get_subscription_schedule(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Schedule ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SubscriptionScheduleResponse](../../models/subscriptionscheduleresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## cancel_subscription_schedule

Use when cancelling a scheduled change (e.g. customer changed mind). Identify by schedule ID in path or by subscription ID + schedule type in body.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelSubscriptionSchedule" method="post" path="/v1/subscriptions/schedules/{schedule_id}/cancel" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.cancel_subscription_schedule(schedule_id_param="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `schedule_id_param`                                                                                          | *str*                                                                                                        | :heavy_check_mark:                                                                                           | Schedule ID (optional if using request body)                                                                 |
| `schedule_id`                                                                                                | *Optional[str]*                                                                                              | :heavy_minus_sign:                                                                                           | schedule_id is the ID of the schedule to cancel (optional if subscription_id and schedule_type are provided) |
| `schedule_type`                                                                                              | [Optional[models.SubscriptionScheduleChangeType]](../../models/subscriptionschedulechangetype.md)            | :heavy_minus_sign:                                                                                           | N/A                                                                                                          |
| `subscription_id`                                                                                            | *Optional[str]*                                                                                              | :heavy_minus_sign:                                                                                           | subscription_id is the ID of the subscription (required if schedule_id is not provided)                      |
| `retries`                                                                                                    | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                             | :heavy_minus_sign:                                                                                           | Configuration to override the default retry behavior of the client.                                          |

### Response

**[models.CancelScheduleResponse](../../models/cancelscheduleresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |

## list_subscription_schedules

Use when listing scheduled changes for a subscription (e.g. upcoming plan change or renewal). Returns all schedules for that subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="listSubscriptionSchedules" method="get" path="/v1/subscriptions/{subscription_id}/schedules" -->
```python
from tirdad_sdk import Tirdad


with Tirdad(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as tirdad:

    res = tirdad.subscriptions.list_subscription_schedules(subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `subscription_id`                                                   | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetPendingSchedulesResponse](../../models/getpendingschedulesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.TirdadDefaultError | 4XX, 5XX                         | \*/\*                            |