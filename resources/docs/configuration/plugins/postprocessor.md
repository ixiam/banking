Active postprocessors are being checked for whether they are likely to be
executed (skipping contribution-related checks, since there aren't any
contributions at preview time). The contribution-related checks are being
skipped (since there aren't any contributions at preview time). A preview for
each to-be-executed postprocessor is shown in each suggestion inside a collapsed
accordion element in the top-right corner of each suggestion. When collapsed,
only the number of to-be-executed post processors is shown (e.g. "2 Post
processors"). Expanding the accordion will place it below the suggestion markup
and display whatever markup post processors are providing, or only their name,
if they don't have a specific implementation for previewing.

After confirming a suggestion, the visualized result will include output
generated by post processors that have been executed. This is dependent on the
actual post processor and should explicitly state what has been done. For post
processors not providing such specific output, a generic message is being shown,
stating that the post processor _might have been executed_, since CiviBanking
can not reliably know genericly whether a post processor has done anything.

!!! note
    This section is yet to be completed.

    TODO: Describe generic configuration properties for required values, value
    propagation, automatic execution, etc.

## Bank Accounts PostProcessor

!!! note
    This section is yet to be completed.

## Update Address PostProcessor

!!! note
    This section is yet to be completed.

## Membership Extension Postprocessor

You can extend a membership when a payment is recorded with CiviBanking or when
a payment is set to completed by creating a _Membership Extension post
processor_.

### Configuration options

Below a list of the possible configuration options.

| Option                           | Possible Values                          | Default         | Description                                                                                                                                                                                                                                                      |
|----------------------------------|------------------------------------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `financial_type_ids`             | _list of ids_                            | 2 (Member Dues) | Only extend a membership when the payment has this financial type                                                                                                                                                                                                |
| `contribution_status_ids`        | _list of contribution status ids_        | 1 (Completed)   | Only extend a membership when the payment has this status                                                                                                                                                                                                        |
| `payment_instrument_ids`         | _list of payment instrument ids          | _empty_         | Only extend a membership when the payment is recorded with one of those payment instruments                                                                                                                                                                      |
| `payment_instrument_ids_exclude` | _list of payment instrument ids          | _empty_         | Only extend a membership when the payment is *not* recorded with one of those payment instruments                                                                                                                                                                |
| `find_via_contact`               | 1 / 0                                    | 1               | Find a membership based on the contact of the payment                                                                                                                                                                                                            |
| `find_via_payment`               | 1 / 0                                    | 1               | Find a membership through the link between the payment and the membership. Only useful when you are updating existing contributions                                                                                                                              |
| `find_via_btxfield`              | _empty_ or _field name of membership id_ | membership_id   | Find the membership by a field in the banking transaction. Only useful when other matchers/importers/post processors set a field in the banking transaction                                                                                                      |
| `filter_current`                 | 1 / 0                                    | 1               | Only update a membership when it has a current status. You can set the class of status under Administer -> CiviMember -> Membership Status Rules                                                                                                                 |
| `filter_minimum_amount`          | _empty_ or True or a monetary amount     | True            | Only extend a membership when the payment has the minimum amount of the membership type or when the payment has the minum amount specified here. You can also disable the check for minimum amount                                                               |
| `filter_membership_types`        | _list of ids_                            | _empty_         | If set only extend memberships of this type                                                                                                                                                                                                                      |
| `filter_max_end_date`            | _date_                                   | 3 months        | Membership end date should not be after 3 months of contribution receive date                                                                                                                                                                                    |
| `extend_by`                      | _period_ or strtotime offset             | period          | When set to period the membership is extend by the membership type period definition. If set to a strtotime value (e.g. +1 month) it is extended by this value                                                                                                   |
| `extend_from`                    | min or end_date or payment_date          | min             | When set to _payment_date_ the membership is extended from the contribution receive date. If set to _end_date_ the membership is extended by the end date of the membership. If set to _min_ then it is extended by the minmum value of end_date or payment_date |
| `align_end_date`                 | next_last or last_last                   | _empty_         | _Not sure how this option works_                                                                                                                                                                                                                                 |
| `create_if_not_found`            | 1 / 0                                    | 0               | Create a new membership when no membership is found                                                                                                                                                                                                              |
| `create_type_id`                 | _id_                                     | 1               | When a new membership is created give it this membership type                                                                                                                                                                                                    |
| `create_start_date`              | receive_date, next_first, last_first     | receive_date    | _Not sure how this option works_                                                                                                                                                                                                                                 |
| `create_source`                  | _any text_                               | CiviBanking     | This is the value set to the source of the membership when a new one is created                                                                                                                                                                                  |
| `link_as_payment`                | 1 / 0                                    | 1               | When set the contribution is linked to the membership                                                                                                                                                                                                            |

### Example configuration

Below is an example configuration for this post processor.

```json
{
  "financial_type_ids": [1],
  "contribution_status_ids": [2],
  "payment_instrument_ids": [],
  "payment_instrument_ids_exclude": [],
  "find_via_contact": 1,
  "find_via_payment": 1,
  "find_via_btxfield": "membership_id",
  "filter_current": 1,
  "filter_minimum_amount": 1,
  "filter_membership_types": [],
  "filter_max_end_date": "3 months",
  "extend_by": "period",
  "extend_from": "end_date",
  "link_as_payment": 0
}
```

## MembershipPayment PostProcessor

!!! note
    This section is yet to be completed.

## API PostProcessor

!!! note
    This section is yet to be completed.

## Contact Deceased PostProcessor

!!! note
    This section is yet to be completed.

## Recurring Contribution Fails PostProcessor

!!! note
    This section is yet to be completed.


