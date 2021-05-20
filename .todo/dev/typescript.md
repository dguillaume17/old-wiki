vs code
    "typescript.preferences.importModuleSpecifier": "relative"

XRegExp
    npm install xregexp
    

    ```json
    {
        ...
        "compilerOptions": {
            ...
            "esModuleInterop": true
        }
    }
    ```


```typescript
enum MyEnum {
    xxx = "xxx",
    yyy = "yyy",
    zzz = "zzz",
}

type myType1 = {-readonly [key in keyof typeof MyEnum]?: number };
type myType2 = Partial<Record<keyof typeof MyEnum, number>>;


const test: myTest2 {
    xxx: 1,
    yyy: 2
};

```


```typescript
enum MyEnum {
    xxx = "xxx",
    yyy = "yyy",
    zzz = "zzz",
}


Object.keys(MyEnum).filter(x => !isNaN(Number(x))).map(x => Language[x])
```