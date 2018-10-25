---
title: Idiainjectedsource::get_source |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2966405dfe3bb7e6134f5ef35e55b30ef6c66c6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909909"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
ソース コードのバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cbData`  
 [in]データ バッファーのサイズを表すバイトの数。  
  
 `pcbData`  
 [out]返されたバイト数を表すバイトの数を返します。 場合`data`は`NULL`、し`pcbData`はデータのバイトの合計数を使用できます。  
  
 `data[]`  
 [out]ソース バイトで格納されるバッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)