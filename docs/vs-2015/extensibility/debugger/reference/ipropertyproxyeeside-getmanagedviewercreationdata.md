---
title: IPropertyProxyEESide::GetManagedViewerCreationData |Microsoft Docs
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
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b5c8899b10907927fdc9b88b94ed9d87d8d1106
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296817"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

そのビューアーをインスタンス化するために、このプロパティの種類ビューアーに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

