---
title: IEEDataStorage::GetData |Microsoft Docs
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
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d23ecbc348d4aab4fdbbb83abaaba54fdad345
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751086"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

オブジェクトから指定したバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dataSize`  
 [in]取得するバイト数 (、`data`配列が、少なくともこのバイト数で保持する必要があります)。  
  
 `sizeGotten`  
 [out]実際に取得するバイト数を返します。  
  
 `data`  
 [入力、出力]要求されたデータと共に格納する配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドの推奨される使用では、取得するプロセス内のバイトをスキップする方法がないために、ローカル配列にすべてのデータ バイトを取得します。 この場合は、パラメーター`dataSize`値によって返される、 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

