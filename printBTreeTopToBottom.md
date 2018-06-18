## 宽度优先打印二叉树

```javascript
const preOrder = [];
        for(let i=0;i<10;i++){
            preOrder[i]=Math.floor(Math.random()*100);
        }
        const inOrder  = preOrder.slice();
        preOrder.sort(function(){
            return Math.random()-Math.random();
        });
        function BTree(value){
            this.data = value;
            this.left = null;
            this.right = null;
        }
        const generateBTree = (preOrder,inOrder) =>{
            
            if(preOrder.length==1) return new BTree(preOrder[0]);

            const node = new BTree(preOrder[0]);
            
            for(var i = 0;i<inOrder.length;i++){
                if(node.data==inOrder[i]){
                    
                    break;
                }
            }

            const left = i;
            const right = preOrder.length-1-i;
            
            if(left>=1){
                const leftPre = preOrder.slice(1,i+1);
                const leftIn = inOrder.slice(0,i);
                
                node.left = generateBTree(leftPre,leftIn);
            }

            if(right>=1){
                const rightPre = preOrder.slice(i+1);
                const rightIn = inOrder.slice(i+1);
                node.right = generateBTree(rightPre,rightIn);
                
            }
            return node;
        }
        
        
        const printBTreeTopToBottom = (Btree)=>{
            if(!BTree) return;
            const deque = [Btree];
            let node;
            while(deque.length){
                node = deque.shift();
                console.log(node.data);
                if(node.left){
                    deque.push(node.left);
                }
                if(node.right){
                    deque.push(node.right)
                }
                
            }
        }

        printBTreeTopToBottom(generateBTree(preOrder,inOrder))
```

