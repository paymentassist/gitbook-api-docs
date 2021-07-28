# Changelog

## 2021-07-28

### Added

* We added the `multi_plan` parameter to the [/begin](methods/begin.md) endpoint.
* We added the `qr_code` parameter to the [/begin](methods/begin.md) endpoint.

## 2021-05-25

### Changed

* To better support off-session workflows, the `success_url` and `failure_url` params are no longer required on calls to the [/begin](methods/begin.md#begin-application) endpoint.

## 2020-11-20

### Added

* We added the ability to modify a pending applications `expiry` via the [/update](methods/update.md) endpoint.

## 2020-10-13

### Changed

* The [/account](methods/account.md) and [/update](methods/update.md) endpoints have now graduated to GA on the live environment.

## 2020-10-07

### Added

* We added a new [/account](methods/account.md) endpoint \(in preview mode\) that returns account level information, such as available plan types.

## 2020-10-06

### Added

* We added a new [/update](methods/update.md) endpoint \(in preview mode\) for altering previously submitted application parameters. Currently, we only support altering the `order_id` \(e.g. for updating a temporary order ID with a final invoice number\).
* We added support for [Webhooks](webhooks.md) \(in preview mode\).
* We added this Changelog.

### Changed

* We now return additional response properties on the application [/status](methods/status.md) endpoint in relation to invoice upload requirement/status.

## 



