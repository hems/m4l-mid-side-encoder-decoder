## Why I'm creating this project/video

I just watched [this great tutorial named "The Magic Of Mid Side"](https://www.youtube.com/watch?v=dD6_Bajj2DI&t=1s&ab_channel=DanWorrall
) by [Dan Worrall](https://www.youtube.com/c/DanWorrall) ( if you don't know Dan, you should SUBSCRIBE to him and "press the bell" to get
all notifications as his content is really incredible ), and I thought it would be an excellent exercise to recreate the ENCODER / DECODER
for M/S using Max4Live.

As Dan outlined in the video, the ENCODER and DECODER algorithm is pretty much the same... The only detail is that when ENCODING, you probably will
want to divide the signal by 2 ( aka multiply it by 0.5 ) for that reason
I have created two devices:
 ENCODER, starts with 0.5 multiplication of the signal 
DECODER,  starts with 1.0 multiplication ( won't change the gain ) of the signal.

For a more feature-rich solution, you probably should use [Voxengo MSED](https://www.voxengo.com/product/msed/)
instead which will not only ENCODE / DECODE to/from M/S but also give you a super polished UI.

Have stereo fun!

## Wait... How it works?

As explained by Dan in [his video](https://www.youtube.com/watch?v=dD6_Bajj2DI&t=1s&ab_channel=DanWorrall):
 - to encode to MID we will sum L and R
 - to encode to SIDE we will subtract R from L

This will likely clip your MID channel, in order to avoid clipping we will half the gain before encoding

ENCODE TO M/S
------
mid = ( L + R ) * 0.5

sid = ( L - R ) * 0.5

To decode the signal we will reverse what we have done in the ENCODER

DECODE TO L/R
------
L = mid + sid

R = mid - sid

DECODE TO L/R ( expanded version )
------
L = L + R + ( L - R )

R = L - R - ( L - R )

## Why would I want that?

Dan explains really well why you would want to do that on his video, [check it out](https://www.youtube.com/watch?v=dD6_Bajj2DI&t=1s&ab_channel=DanWorrall
) and don't forget to subscribe to Dan's channel!