---
title: IPropertyProxyEESide::InitSourceDataProvider |Microsoft Docs
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
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dde77e3468374d0e82aaaf3135407992171c837
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545165"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IPropertyProxyEESide::InitSourceDataProvider](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider)します。  
  
このオブジェクトのソース データを初期化し、初期のデータを格納するオブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dataOut`  
 [out]返します、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)オブジェクト  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが返すことができますので、オブジェクトを初期化するために必要なことすべて、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)オブジェクトのデータのインターフェイス。 これにより、オブジェクトのデータを表示および、許可されている場合は、型のビジュアライザーによって変更できます。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

