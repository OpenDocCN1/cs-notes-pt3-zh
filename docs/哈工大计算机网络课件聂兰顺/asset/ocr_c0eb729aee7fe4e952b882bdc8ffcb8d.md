# Selective Repeat: 发送方/接收方窗口

send_base

nextseqnum

window size
N

(a) sender view of sequence numbers

already ack'ed

usable, not yet sent

sent, not yet ack'ed

not usable

rcv_base

window size
N

(b) receiver view of sequence numbers

out of order (buffered) but already ack'ed

acceptable (within window)

Expected, not yet received

not usable