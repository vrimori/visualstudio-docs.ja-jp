---
title: IPropertyProxyEESide::GetManagedViewerCreationData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39e32c5c650faa30c5a164e3a15bd26fc058e010
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917329"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
そのビューアーをインスタンス化するために、このプロパティの種類ビューアーに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `assemName`  
 [out]このオブジェクトを保持しているアセンブリの名前を返します。  
  
 `assemBytes`  
 [out]返します、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) (これは、null 値をバイトが使用できない場合)、このオブジェクトのアセンブリのバイト数を格納しているオブジェクト。  
  
 `assemPdb`  
 [out]返します、`IEEDataStorage`シンボルを含むオブジェクトは、(これは、null 値をシンボル ストアが使用できない場合)、このオブジェクトの情報を格納します。  
  
 `className`  
 [out]このオブジェクトを含むクラスの名前を返します。  
  
 `alr`  
 [out]値を返します、 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)アセンブリの場所を示す列挙値。  
  
 `replacementOk`  
 [out]0 以外の値を返します (`TRUE`) このオブジェクトの値を変更できる場合は 0 (`FALSE`) オブジェクトが読み取り専用である場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、管理対象のビューアーをインスタンス化する型のビジュアライザーによって使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)