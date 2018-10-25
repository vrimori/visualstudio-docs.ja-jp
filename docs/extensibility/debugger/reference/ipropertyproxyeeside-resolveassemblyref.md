---
title: IPropertyProxyEESide::ResolveAssemblyRef |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7711d185e92b0cc8a29070aa78a4acff835df33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846942"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
指定したマネージ アセンブリの参照の場所を決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `assemName`  
 [in]解決するのには、アセンブリの名前です。  
  
 `assemBytes`  
 [out]返します、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)参照に関連付けられているアセンブリのバイト数を格納しているオブジェクト。  
  
 `assemPdb`  
 [out]返します、`IEEDataStorage`シンボルを含むオブジェクトがこの参照に関連付けられているデータを格納します。  
  
 `assemLocation`  
 [out]この参照のパスの場所を返します。  
  
 `alr`  
 [out]値を返します、 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)この参照のアセンブリの場所を示す列挙値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 通常、このメソッドはカスタム式エバリュエーターでは実装されません。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)