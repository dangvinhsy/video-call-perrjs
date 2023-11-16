# VideoCall_PeerJS

## Luồng xử lý

- User gửi một `request` đến Server gồm các thông tin cơ bản như:
    - `calling-id: (int)`: gửi cuộc gọi đến cho ai
    - `caller-id: (int)` : người nào gửi cuộc gọi
    - `call-room-token (String)`: token phòng chat
- Khi server nhận được thông tin sẽ trả về cho `caller` một thông báo rằng đang thực hiện gọi đến `calling`. Đồng thời sẽ gửi thông báo cho `calling` rằng có người gọi đến
- Khi `calling` nhận được thông báo thực hiện [join]() vào phòng chat video `call-room-token`:
- Khi một trong hai thoát khỏi phòng chat video, client sẽ gửi thông tin lên server để tiến hành `destroy` id phòng chat đó.

Ví dụ cụ thể:

dangth calling nhuomtv...

dangth request to server:

```js
body
------
{
    calling-id: 1,  // id user được gọi
    caller-id: 2    // id user thực hiện gọi & id phòng chat
    call-room-token: ey53446hjhbj
}
```

server xử lý:
- Send socket to user có id là `1`: `Fullname` đang gọi...
- Send socket to user có id là `2`: Đang gọi `Fullname`....

Calling xử lý:
- Join vào room có id là `2`

## Công nghệ 
- WebRTC
- PeerJS
- StockJS/StomJS