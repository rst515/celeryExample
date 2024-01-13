Python Celery tutorial based on https://medium.com/swlh/python-developers-celery-is-a-must-learn-technology-heres-how-to-get-started-578f5d63fab3

In summary, there are three server elements required:
- [Redis](https://redis.io/topics/quickstart) message broker running in background for the queue

    `> redis-server`
- Django web server adding new tasks to the queue (the task in this example is in celery.py but could be in tasks.py)

    `> python manage.py runserver`
- Celery worker to asynchronously process tasks

  `celery -A celery_tutorial.celery worker --loglevel=info`

To add the task to the queue:

`> python manage.py shell`

```
from celery_tutorial.celery import debug_task 
debug_task.delay()
<AsyncResult: fe261700-2160-4d6d-9d77-ea064a8a3727>
```