---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

構成ストリームの現在位置から始めて命令を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### パラメーター  
 `dwInstructions`  
 \[逆アセンブル\] 命令数。  この値は`prgDisassembly` の配列の最大長。  
  
 `dwFields`  
 \[入力\] `prgDisassembly` のフィールドが設定されるかを示す [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) の列挙体のフラグの組み合わせ。  
  
 `pdwInstructionsRead`  
 \[出力\] 実際に逆アセンブル命令数を返します。  
  
 `prgDisassembly`  
 \[入力\] 逆アセンブルしたコードが格納されます [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造体の配列逆アセンブル手順ごとに 1 回の構造体。  この配列の長さが `dwInstructions` のパラメーターによって指定されます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 現在のスコープで使用できる命令の最大数は [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) のメソッドを呼び出して取得できます。  
  
 次の手順が読み込まれた現在位置を [シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) のメソッドを呼び出すことで変更できます。します。  
  
 `DSF_OPERANDS_SYMBOLS` フラグは `dwFields` のパラメーターの `DSF_OPERANDS` フラグに順序を逆アセンブルするときにシンボル名を使用する必要があることを示すために追加できます。  
  
## 参照  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)