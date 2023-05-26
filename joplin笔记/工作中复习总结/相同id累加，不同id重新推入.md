> 有的时候会遇到一些问题，比如用户送礼物，相同的用户id和相同的礼物id则将礼物的价格累加，如果不同则推入到数组作为新的一项。
```javascript
addGiftRank(msg: IMbo.INobleMessage | IMbo.IGiftMessage | IMbo.ISuperChatMessage) {
        if (msg.cash <= 0) {
            return;
        }
        let data: DirectorData = {
            userAvatar: msg.userAvatar,
            userId: msg.userId,
            userName: msg.userName,
            cash: msg.cash,
            lastrank: -1,
            variate: 'new',
            time: Date.now(),
        }
        let bool = false;
        for (let i = 0; i < this.mTotleData.length; i++) {
            const obj = this.mTotleData[i];
            // 如果用户名和id相同时，礼物的价格叠加
            if (obj.userName == data.userName && data.userId == obj.userId) {
                obj.cash += data.cash;
                obj.time = data.time;
                data = obj;
                bool = true;
                break;
            }
        }

        if (!bool) {
            this.mTotleData.push(data);
        }

        this.mTotleData.sort((a: DirectorData, b: DirectorData) => {
            if (a.cash == b.cash) {
                return (a.time - b.time);
            } else {
                return (b.cash - a.cash);
            }
        })
    }
```