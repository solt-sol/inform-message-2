# inform-message-2
Код с изменениями:

```
async def once_done(sink: discord.sinks, channel: discord.TextChannel, *args):
    recorded_users = [
        f"<@{user_id}>"
        for user_id, audio in sink.audio_data.items()
    ]
    text = "Сними коментарий через 2 строчки вниз"
    await sink.vc.disconnect() 
    files = [discord.File(audio.file, f"{user_id}.{sink.encoding}") for user_id, audio in sink.audio_data.items()]
    file = files[0]
    text = client.speech(file, {'Content-Type': 'audio/wav'})
    await channel.send(text, files=files)  
```

Ошибка:

```
Exception in thread Thread-3 (recv_audio):
Traceback (most recent call last):
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\threading.py", line 1009, in _bootstrap_inner
    self.run()
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\threading.py", line 946, in run
    self._target(*self._args, **self._kwargs)
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\discord\voice_client.py", line 802, in recv_audio
    result = callback.result()
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\concurrent\futures\_base.py", line 446, in result
    return self.__get_result()
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\concurrent\futures\_base.py", line 391, in __get_result
    raise self._exception
  File "C:\Users\RBT\Documents\cc\informi.py", line 75, in once_done
    text = client.speech(file, {'Content-Type': 'audio/wav'})
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\wit\wit.py", line 89, in speech
    resp = req(self.logger, self.access_token, 'POST', '/speech', params,
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\wit\wit.py", line 34, in req
    rsp = requests.request(
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\requests\api.py", line 59, in request
    return session.request(method=method, url=url, **kwargs)
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\requests\sessions.py", line 587, in request
    resp = self.send(prep, **send_kwargs)
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\requests\sessions.py", line 701, in send
    r = adapter.send(request, **kwargs)
  File "C:\Users\RBT\AppData\Local\Programs\Python\Python310\lib\site-packages\requests\adapters.py", line 523, in send
    for i in request.body:
TypeError: 'File' object is not iterable
```
