---
title: "IDiaStackWalkHelper::pdataForVA |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4925a4a37395dd53fabb1d8d7ba7f80bc5cc6c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
仮想アドレスに関連付けられている PDATA データ ブロックを返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `va`  
 [in]取得するデータの仮想アドレスを指定します。  
  
 `cbData`  
 [in]取得するバイトのデータのサイズ。  
  
 `pcbData`  
 [out]取得されたバイト数では、データの実際のサイズを返します。  
  
 `pbData`  
 [入力、出力].要求されたデータが入力バッファー。 ことはできません`NULL`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`指定されたアドレスの PDATA がない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 PDATA (".pdata"という名前の部分)、コンパイル単位の関数の例外処理に関する情報が含まれています。  
  
 呼び出し元は、データの量が、呼び出し元には、データの量は利用できるように依頼する必要があるないために返されるを認識します。 したがって、エラーを返す場合はこのメソッドを実装するための許容は、`pbData`パラメーターは`NULL`します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)