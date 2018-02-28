---
title: "IDebugDisassemblyStream2::Read |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: edc41da40c4f0c292523ed338419fbc4a7253dcf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
逆アセンブル ストリーム内の現在位置から開始する指示を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwInstructions`  
 [in]逆アセンブルする命令の数。 この値はの最大長でも、`prgDisassembly`配列。  
  
 `dwFields`  
 [in]フラグの組み合わせ、 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)のどのフィールドを示す列挙`prgDisassembly`に記入することができます。  
  
 `pdwInstructionsRead`  
 [out]実際に逆アセンブルの命令の数を返します。  
  
 `prgDisassembly`  
 [out]配列[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造体を逆アセンブルしたコード、逆アセンブルされた命令ごとに 1 つの構造が入力されます。 この配列の長さは、によって決まります、`dwInstructions`パラメーター。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 呼び出して、現在のスコープで使用可能な命令の最大数を取得できます、 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)メソッドです。  
  
 次の命令がから読み取られる現在の位置を呼び出すことにより変更することができます、[シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)メソッドです。  
  
 `DSF_OPERANDS_SYMBOLS`にフラグを追加することができます、`DSF_OPERANDS`フラグ、`dwFields`パラメーターを逆アセンブルするときにシンボル名を使用することを示します。  
  
## <a name="see-also"></a>参照  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)