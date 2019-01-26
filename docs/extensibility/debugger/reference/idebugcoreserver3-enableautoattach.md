---
title: IDebugCoreServer3::EnableAutoAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3c3132239ec684f947e702ce59f0a269095f990
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031186"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
指定されたデバッグ エンジンの自動アタッチを使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
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