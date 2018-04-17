---
title: IEEDataStorage::GetData |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ddbc77950396df743b88ce3b6c1a94bbeaf8126
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
オブジェクトから指定したバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [out]実際に取得されるバイト数を返します。  
  
 `data`  
 [入力、出力].要求されたデータを使用して入力する配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 取得プロセス内のバイトをスキップする方法がないために、ローカルの配列にすべてのデータ バイトを取得するは、このメソッドを使用してください。 この場合は、パラメーター`dataSize`値によって返される、 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)