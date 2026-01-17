# Phone Numbers

Manage phone numbers configured in your PIA Platform account.

## List phone numbers

- Method: GET
- Path: `/v1/phone-numbers`

### Parameters

- `page_size` (integer, optional): 1-100. Default: 20.
- `page_token` (string, optional): Pagination token.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
numbers = client.phone_numbers.list(page_size=20)
```

## Get phone number

- Method: GET
- Path: `/v1/phone-numbers/{phone_number_id}`

### Parameters

- `phone_number_id` (string, required): Phone number record ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
number = client.phone_numbers.get("phone_number_id")
```

## Create phone number

- Method: POST
- Path: `/v1/phone-numbers`

### Parameters

Shared fields:

- `phone_number` (string, required): E.164 phone number with country code.
- `provider` (string, required): `sip`, `pia`, or `twilio`.
- `friendly_name` (string, optional): Label for internal use.
- `inbound_agent_id` (string, optional): Agent for inbound calls.
- `outbound_agent_id` (string, optional): Agent for outbound calls.

SIP provider fields:

- `sip_termination_uri` (string, optional): SIP URI for termination.
- `sip_trunk_username` (string, optional): SIP trunk username.
- `sip_trunk_password` (string, optional): SIP trunk password.
- `sip_infra_region` (string, optional): `global`, `bd`, or `bd_link3`.

Twilio provider fields:

- `twilio_account_sid` (string, required): Twilio account SID.
- `twilio_auth_token` (string, required): Twilio auth token.

### SDK example (SIP)

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "phone_number": "+14155552671",
    "provider": "sip",
    "friendly_name": "Support Line",
    "sip_termination_uri": "sip:example@sip.provider.com",
    "sip_trunk_username": "user",
    "sip_trunk_password": "pass",
}
created = client.phone_numbers.create(payload)
```

## Update phone number

- Method: PATCH
- Path: `/v1/phone-numbers/{phone_number_id}`

### Parameters

Common fields:

- `friendly_name` (string, optional): Updated label.
- `inbound_agent_id` (string, optional): Updated inbound agent.
- `outbound_agent_id` (string, optional): Updated outbound agent.

SIP fields:

- `sip_termination_uri` (string, optional)
- `sip_trunk_username` (string, optional)
- `sip_trunk_password` (string, optional)

Twilio fields:

- `twilio_account_sid` (string, optional)
- `twilio_auth_token` (string, optional)

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
updated = client.phone_numbers.update("phone_number_id", {"friendly_name": "Main Line"})
```

## Delete phone number

- Method: DELETE
- Path: `/v1/phone-numbers/{phone_number_id}`

### Parameters

- `phone_number_id` (string, required): Phone number record ID.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
client.phone_numbers.delete("phone_number_id")
```
