#顺时针输出矩阵

#####  问题：给定一个矩阵，顺时针输出其中的元素
-----

 ![](https://github.com/EdwinMei/algorithm/raw/master/images/printMatrix.png) 


解决算法关键是需要找到一个循环，从上图可以看出，每次顺时针输出都可以看成是(0,0),(1,1)···(n,n)，为起点的一圈，当顺时针起始点(n,n)超过了矩阵横纵坐标的一半时，循环结束。

顺时针输出一圈一般需要四步（第三步前提下，终止行号比起始位置至少大2），left -> right，top-> bottom，right -> left，bottom -> top，但是也可能是三步（终止行列号大于起始位置）、两步（终止行号大于起始位置）、甚至一步（只有一行）就能解决。

```javascript
//顺时针输出矩阵
const printMatrixClockwisely = (matrix,row,col)=>{
	//处理输入矩阵为空
    if(!matrix&&!matrix[0]) return;
	
    let start = 0;

    while(row>start*2&&col>start*2){
        printClockwisely(matrix,row,col,start);
        ++start;
    }

}

const printClockwisely = (matrix,row,col,start)=>{
    const y = row-1 - start;//坐标y
    const x = col-1 - start;//坐标x

    //left -> right
    for(let i = start;i<=x;i++){
        console.log(matrix[start][i])
    }
    console.log('left -> right')
    if(start<y){
        //top->bottom
        for(let i = start + 1;i<=y;i++){
            console.log(matrix[i][x])

        }
        console.log('top->bottom')
        if(start<x){
            //right -> left 
            for(let i = x-1;i>=start;i--){
                console.log(matrix[y][i])
            }
            console.log('right -> left')
            if(start+1<y){
                //bottom -> top
                for (let i = y-1; i > start; i--) {
                    console.log(matrix[i][start])                            
                }
                console.log('bottom -> top')
            }
        }
    }
}


const initMatrix = (row,col)=>{
    let matrix = [];
    for(let i=0;i<row;i++){
        matrix[i] = [];
        for(let j = 0;j<col;j++){
            matrix[i][j] = Math.floor(Math.random()*10);
        }
    }
    console.log(matrix)
    printMatrixClockwisely(matrix,row,col)
}

initMatrix(8,10)
```

