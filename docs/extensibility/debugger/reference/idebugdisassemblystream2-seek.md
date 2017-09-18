---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定した位置に対する命令の指定した数値の逆アセンブル\] ストリームの読み取りポインターを移動します。  
  
## 構文  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### パラメーター  
 `dwSeekStart`  
 \[入力\] シーク プロセスを開始する相対位置を指定する [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) の列挙体の値。  
  
 `pCodeContext`  
 \[入力\] シーク操作が相対的であること [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) にコード コンテキスト。  このパラメーターは`dwSeekStart``dwSeekStart` のみ `dwSeekStart` \= `SEEK_START_CODECONTEXT` 使用されています ; それ以外の場合このパラメーターは無視されnull 値を指定できます。  
  
 `uCodeLocationId`  
 \[入力\] シーク操作が相対位置にあるコードの識別子。  このパラメーターが `dwSeekStart``dwSeekStart``dwSeekStart` \= `SEEK_START_CODELOCID` 使用されています ; それ以外の場合このパラメーターは無視され0 に設定します。  コード位置の識別子について [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) のメソッドについては" 解説 " を参照してください。  
  
 `iInstructions`  
 \[入力\] `dwSeekStart` で指定した場所に移動して関連する命令数。  この値は後方に値が負になる場合があります。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` シークの場所が使用可能な命令リストを越えるポイントにある `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 リストの先頭がリストの最初の命令に読み取られた場所に設定される前にシークある場所に存在します。  リストの末尾がリストの最後の命令に読み取られた場所に設定すると表示の場所にある場合は。  
  
## 参照  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)