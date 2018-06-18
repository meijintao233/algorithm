#栈的序列

#### 问题：给定一个栈的压入和另一个序列，判断该另一个序列是否为该压入序列的弹出序列

---



```javascript
const stackSeq = (stackPush,stackPop)=>{
            
    if(!stackPush||!stackPop||stackPop.length!=stackPush.length) return false;

    const assit = [];
    let pPop = 0;
    let pPush = 0;

    while(pPop<stackPop.length){
        if(assit[assit.length-1]!=stackPop[pPop]){
            if(pPush<stackPush.length){
                assit.push(stackPush[pPush++]);
            }else{
                return false;
            }
        }else{
            assit.pop();
            pPop++; 
        }
    }
    return true;            
}
```



​                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      