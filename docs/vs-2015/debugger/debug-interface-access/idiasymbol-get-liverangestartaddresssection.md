---
title: IDiaSymbol::get_liveRangeStartAddressSection |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49985c1ca0ddb1b20a3b498a3dadba45b58e6c0b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538825"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaSymbol::get_liveRangeStartAddressSection](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection)します。  
  
ローカル シンボルの有効範囲の開始アドレスのセクションの一部を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `section`  
 [out]アドレス範囲の開始のセクションの一部を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  返されたエラー コードは、シンボルにライブの範囲の情報がないことを意味します。  
  
## <a name="remarks"></a>Remarks  
 セクションとオフセットで構成されるアドレスは、シンボルの有効範囲の先頭です。  
  
 アドレスのオフセットの部分を取得する[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



