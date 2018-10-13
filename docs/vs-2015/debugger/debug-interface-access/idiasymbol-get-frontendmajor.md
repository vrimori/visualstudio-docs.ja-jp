---
title: Idiasymbol::get_frontendmajor |Microsoft Docs
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
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c44e1ba2d21b7063cc09379ee5e2120b9ba35231
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272949"
---
# <a name="idiasymbolgetfrontendmajor"></a>IDiaSymbol::get_frontEndMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

フロント エンドのメジャー バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_frontEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]フロント エンドのメジャー バージョン番号を返します。 「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>Remarks  
 コンパイラは通常の 2 つの主な要素で構成されます。 中間形式を解析してソース コードを処理するフロント エンド (パーサー) と、バック エンド (コード ジェネレーター) アセンブリに中間形式を変換します。 これは、フロント エンド、バックエンドとは異なるバージョンが珍しくありません。  
  
 フロント エンドまたはバックエンドのバージョン番号は 3 つの部分で構成されます:\<メジャー >.\<マイナー >。\<ビルド > ここで、\<主要な >、メジャー バージョン番号は、\<マイナー > はマイナー バージョン番号、および\<ビルド > ビルド番号です。 たとえば、13.10.3077 です。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



