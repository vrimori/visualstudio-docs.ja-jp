---
title: IDebugModule2::ReloadSymbols_Deprecated |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a8c42ddcde84524819f2c8f828fa72c8617d423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536088"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugModule2::ReloadSymbols_Deprecated](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated)します。  
  
互換性のために残されています。 使用しないでください。 このモジュールのシンボルを再読み込みします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszUrlToSymbols`  
 [in]シンボル ストアへのパス。  
  
 `pbstrDebugMessage`  
 [out][モジュール] ウィンドウで、モジュール名の右側に表示されるステータスまたはエラー メッセージなどの情報メッセージを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 デバッグ エンジンは常に返す必要があります`E_FAIL`します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドはサポートされなくなりました。 実装、 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)メソッド代わりにします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

