---
title: "Idialinenumber::get_addressoffset |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_addressOffset method
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 57c5b581551b75893f5bf8a77d3819d0268f8d6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idialinenumbergetaddressoffset"></a>IDiaLineNumber::get_addressOffset
ブロックの開始位置、メモリ アドレスのオフセットの部分を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ブロックの開始位置、メモリ アドレスのオフセットの部分を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="example"></a>例  
  
```C++  
CComPtr< IDiaLineNumber > pLine;  
DWORD offset;  
pLine->get_addressOffset( &offset);  
```  
  
## <a name="see-also"></a>参照  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)