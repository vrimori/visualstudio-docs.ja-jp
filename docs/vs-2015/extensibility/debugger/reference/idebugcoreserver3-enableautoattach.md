---
title: IDebugCoreServer3::EnableAutoAttach |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0823c64e150d306d4613a8df797f11c0785ba762
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774498"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定されたデバッグ エンジンの自動アタッチを使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

