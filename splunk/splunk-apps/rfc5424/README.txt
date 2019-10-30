VERSION
Version 1.1 adds the ability to handle messages formatted according to RFC 6587.

DESCRIPTION
This is an Add-On for syslog data formatted according to the RFC 5424 or RFC 6587 specifications.

INSTALLATION
Set sourcetype="rfc5424_syslog" for all RFC5424 data inputs. This app includes index-time transformations for the "host" field, so should be in place BEFORE data is indexed.

AVAILABLE FIELDS
The following fields are extracted:

prival  - This integer encodes the syslog facility and severity. Use the convert_facility_severity macro, described below, to decode the facility and severity fields.
appname - The field APP-NAME described in RFC5424
procid  - The field PROCID described in RFC5424
msgid   - The field MSGID described in RFC5424
host    - The field HOSTNAME described in RFC5424. NOTE: This field is an index-time transformation

Within a structured data element (i.e., [...]), the following fields are extracted:

sdid            - The field SD-ID described in RFC5424. This field is evaluated as a multi-value field.
key/value pairs - All KV pairs (i.e., field1="value1") are extracted, but are not evaluated as multi-value pairs.

SEARCH TRICKS
To extract the FACILITY and SEVERITY values from the PRIVAL value:
    sourcetype="rfc5424_syslog" | `convert_facility_severity`

To convert FACILITY values into text descriptions:
    sourcetype="rfc5424_syslog" | `convert_facility_severity` | lookup facility_lookup facility

To convert SEVERITY values into text descriptions:
    sourcetype="rfc5424_syslog" | `convert_facility_severity` | lookup severity_lookup severity

KNOWN ISSUES/LIMITATIONS
- Fields which appear more than once in an event (i.e., field1="value1" field1="value2") will not be evaluated as multi-value fields
- Within a structured data block, the SDID is not associated with the local field names; it is simply another multi-value field, "sdid"
- The MSG section of the event, if it exists, is not parsed by this app.
