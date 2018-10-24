---
title: IDebugCoreServer3::EnableAutoAttach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5fc3ab0767a7077860c82acefc9554ba1228cee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831121"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
指定されたデバッグ エンジンの自動アタッチを使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rgguidSpecificEngines`  
 [in]各デバッグ エンジンと自動アタッチをマークするには、Guid の配列。  
  
 `celtSpecificEngines`  
 [in]指定されたエンジン数`rgguidSpecificEngines`します。  
  
 `pszStartPageUrl`  
 [in]自動アタッチするときに使用する開始 URL。  
  
 `pbstrSessionID`  
 [out]自動アタッチがセッションの ID。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`; エラー コードを返します。 1 つのエラー コードは`E_AUTO_ATTACH_NOT_REGISTERED`、auto-attach クラス ファクトリが登録されていないことを示します。  
  
## <a name="remarks"></a>Remarks  
 指定した URL に関連付けられたプログラムが開始されると、指定されたデバッグ エンジンは自動的に開始し、接続されています。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)