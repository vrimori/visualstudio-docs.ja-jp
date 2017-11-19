---
title: "IPropertyProxyEESide::GetManagedViewerCreationData |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc4d81470a1ea15573171a80034efcd6daf720ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
そのビューアーをインスタンス化するのには、このプロパティの種類のビューアーに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
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
 [out]返します、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) (これは、null 値使用可能なバイトがない場合)、このオブジェクトのアセンブリのバイト数を含むオブジェクト。  
  
 `assemPdb`  
 [out]返します、`IEEDataStorage`シンボルを含むオブジェクトは、このオブジェクトの情報を (これは、null 値のシンボル ストアが使用できない場合) を格納します。  
  
 `className`  
 [out]このオブジェクトを含むクラス名を返します。  
  
 `alr`  
 [out]値を返します、 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)アセンブリの場所を示す列挙値。  
  
 `replacementOk`  
 [out]0 以外を返します (`TRUE`) このオブジェクトの値を変更できる場合は 0 (`FALSE`) 場合は、オブジェクトは読み取り専用です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 型のビジュアライザーはこのメソッドを使用して、管理されているビューアーをインスタンス化します。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)