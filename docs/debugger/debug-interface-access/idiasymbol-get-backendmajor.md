---
title: Idiasymbol::get_backendmajor |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf32104654d40f314dc3468eaf28dfded6998df9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942310"
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
コンパイラのバック エンドのメジャー バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_backEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]バック エンドのメジャー バージョン番号を返します。 「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 コンパイラは通常の 2 つの主な要素で構成されます。 中間形式を解析してソース コードを処理するフロント エンド (パーサー) と、バック エンド (コード ジェネレーター) アセンブリに中間形式を変換します。 これは、フロント エンド、バックエンドとは異なるバージョンが珍しくありません。  
  
 フロント エンドまたはバックエンドのバージョン番号は 3 つの部分で構成されます:\<メジャー >.\<マイナー >。\<ビルド > ここで、\<主要な >、メジャー バージョン番号は、\<マイナー > はマイナー バージョン番号、および\<ビルド > ビルド番号です。 たとえば、13.10.3077 です。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)