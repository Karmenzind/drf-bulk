# drf-bulk

Bulk utils for Django REST Framework.

Inspired by and partially based on [django-rest-framework-bulk](https://github.com/miki725/django-rest-framework-bulk). ([Why don't just fork it?]())

# status

in development

- try fix the issues with django-rest-framework-bulk which seems no longer maintained
- be compatible with django-rest-framework-bulk but stop it whenever necessary

# settings

example:

```python
DRF_BULK = {
    "iter_mode": True,
}
```

- iter_mode `dict`

attributes and default values:
    - enabled `True`
    - s_field_name `successful`
    - f_field_name `failed`

By default, the serializer will check the instances and simply finish the request and raise an exception if any instance failed. But if you enable `iter_mode`, the request will continue processing other instances and return two list as follows:

```json
{
    "successful": [
        {
            "attr_a": "xxx",
            "attr_b": "xxx"
        }
    ],
    "failed": [
        {
            "data": {
                "attr_a": "xxx",
            },
            "detail": "'attr_b' is required"
        }
    ]
}
```

This might be useful under some circumstances.

Change the `*_field_name` if you don't like the default field names.

