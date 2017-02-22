---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
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
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムの名前を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### パラメーター  
 `pbstrProgramName`  
 \[入力\] プログラムの名前を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 プログラムの名前はプログラムのパスとプログラムの名前はそのようなパスの一部である可能性がありますが同じではありません。  
  
## 使用例  
 次の例に `CProgram` の単純なオブジェクトに対してこのメソッドを実装する方法を実装するインターフェイスの [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 示します。  `MakeBstr` の関数に BSTR として指定された文字列のコピーを割り当てます。  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## 参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)