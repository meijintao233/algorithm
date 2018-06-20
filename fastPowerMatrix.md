##  矩阵快速幂

```javascript
const initMatrix = (x,y,value)=>{
            const matrix=[];
            for(let i=0;i<x;i++){
                matrix[i] = [];
                for(let j=0;j<y;j++){
                    matrix[i][j] = value|Math.floor(Math.random()*50);
                }
            }
            return matrix;
        }

        const multiply = (x,y,row,col)=>{
            const matrix = initMatrix(3,3,0);
            
            for (let i = 0; i < row; i++) {
                for(let j=0;j< col;j++){
                    for(let k=0;k<col;k++){
                        matrix[i][j] += x[i][k]*y[k][j];
                    }
                }
                
            }
            return matrix;
        }
        
        const fastPoweMatrix = (power,x,res)=>{
            while(power){
                if(power&1){
                    console.log(res)
                    console.log(x)
                    res = multiply(res,x,3,3);
                }
                power>>=1;
                x = multiply(x,x,3,3);
            }
            console.log(res)
        }
        fastPoweMatrix(156,initMatrix(3,3),initMatrix(3,3,1))
```



