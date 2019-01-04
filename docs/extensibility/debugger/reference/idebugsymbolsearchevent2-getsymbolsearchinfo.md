---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f02eba47963dc39e7fa1fc426a762ff9f30a664d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888700"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
シンボルの読み込みプロセスの結果を取得するためのイベント ハンドラーによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pModule`  
 [out]対象のシンボルが読み込まれたモジュールを表す IDebugModule3 オブジェクト。  
  
 `pbstrDebugMessage`  
 [入力、出力]モジュールからすべてのエラー メッセージを含む文字列を返します。 エラーがない場合は、この文字列には、モジュールの名前にはだけが含まれますが、空ではありません。  
  
> [!NOTE]
>  [C++]`pbstrDebugMessage`することはできません`NULL`を解放する必要がありますと`SysFreeString`します。  
  
 `pdwModuleInfoFlags`  
 [out]フラグの組み合わせ、 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)シンボルが読み込まれたかどうかを示す列挙値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ハンドラーが受信すると、 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)イベント モジュールのデバッグ シンボルの読み込みを試行した後、ハンドラーは、その負荷の結果を判断するこのメソッドを呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)