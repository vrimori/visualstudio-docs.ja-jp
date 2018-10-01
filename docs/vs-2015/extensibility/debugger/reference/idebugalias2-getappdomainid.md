---
title: IDebugAlias2::GetAppDomainId |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8a2c766a1ec6fce1856312756adad3c5f234866
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533242"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugAlias2::GetAppDomainId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias2-getappdomainid)します。  
  
アプリケーション ドメインの識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pappDomainId`  
 [out]アプリケーション ドメインの識別子を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメインの識別子変更、アプリケーションが再起動されるたびに、新しいアプリケーション ドメインが作成されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)

