---
title: "IDebugClassField::GetDefaultIndexer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetDefaultIndexer"
helpviewer_keywords: 
  - "IDebugClassField::GetDefaultIndexer メソッド"
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

既定のインデクサーの名前を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```c#  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### パラメーター  
 `pbstrIndexer`  
 \[入力\] 文字列を既定のインデクサー名返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功すると既定のインデクサーがある。  それ以外の場合はエラー コード。  
  
## 解説  
 クラスの既定のインデクサーは配列の `Default` のプロパティにアクセスするのとしてマークされたプロパティです。  これは [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] に固有です。  どのように使用されるか [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] で宣言された既定のインデクサーの例は次のとおりです。  
  
```vb#  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## 参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)