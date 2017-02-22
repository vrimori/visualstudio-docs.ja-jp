---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals メソッド"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドの選択されたローカル変数の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) を表すオブジェクトを取得するローカル スコープまたはコンテキストを選択するデバッグのアドレス。  
  
 `ppLocals`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) にローカルの一覧を返します ; ローカルである場合null 値を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功している場合を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 特定のデバッグのアドレスを含むブロック内で定義されている変数のみを列挙します。  すべてのコンパイラが生成したローカルを含むすべてのローカルに応じて[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) のメソッドを呼び出します。  
  
 メソッドのコンテキストまたはスコープは複数のブロックを含めることができます。  たとえば次の考案されているメソッドは 3 個の範囲は2 種類の内部ブロックとメソッド本体自体が含まれています。  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) のオブジェクトは `func` のメソッド自体を表します。  [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) の `EnumLocals` のメソッドを呼び出します `Inner Scope 1` のアドレスの戻り値に `temp1` の変数を含む列挙型などを設定します。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)