# pytest-interleave
py.test Interleave Plugin

```python

def async_ready():
    wait_for_async()
    yield
    wait_for_async()
    yield
    wait_for_async()


@pytest.mark.interleave(async_ready)
def test_my_long():
    launch_async()
    yield
    assert async_state()
    
    launch_more_async()
    yield
    assert async_state()
    
    launch_even_more_async()
    yield
    assert async_state()


@pytest.mark.interleave(async_ready)
@pytest.mark.parameterize()
def test_my_others():
    launch_async()
    yield
    assert async_state()
    
    launch_more_async()
    yield
    assert async_state()
    
    launch_even_more_async()
    yield
    assert async_state()
```
