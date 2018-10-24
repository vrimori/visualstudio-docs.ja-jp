---
title: IDiaStackWalkHelper::pdataForVA |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 525a19a997d5902da5d69d5804281d472b5d6a26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906222"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

仮想アドレスに関連付けられている PDATA データ ブロックを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in] (バイト) を取得するデータのサイズ。  
  
 `pcbData`  
 [out]取得したバイトでは、データの実際のサイズを返します。  
  
 `pbData`  
 [入力、出力]要求されたデータが入力バッファー。 ことはできません`NULL`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`指定されたアドレスの PDATA がない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 PDATA (".pdata"という名前の部分)、コンパイル単位の関数の例外処理に関する情報が含まれています。  
  
 データの量が、呼び出し元に、データの量は使用を要求する必要がないために返される、呼び出し元が認識しています。 そのため、許容される場合は、エラーを返すには、このメソッドの実装は、`pbData`パラメーターが`NULL`します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)



