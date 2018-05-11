---
title: Idiasymbol::get_backendmajor |Microsoft ドキュメント
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
ms.openlocfilehash: 228b115122481cf939cb7a32db4bfce2178263e4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
コンパイラのバックエンドのメジャー バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_backEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]バックエンドのメジャー バージョン番号を返します。 「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
 コンパイラは通常の 2 つの主な要素で構成されます。 中間形式のソース コードの解析を処理するフロント エンド (パーサー) と、バック エンド (コード ジェネレーター)、アセンブリに中間形式に変換します。 フロント エンドがバックエンドとは異なるバージョンは珍しいことではありません。  
  
 フロント エンドまたはバック エンドにバージョン番号は 3 つの部分で構成されます:\<メジャー >.\<マイナー >。\<ビルド > ここで、\<メジャー > メジャー バージョン番号は、\<マイナー > マイナー バージョン番号と\<ビルド > ビルド番号です。 たとえば、13.10.3077 です。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)