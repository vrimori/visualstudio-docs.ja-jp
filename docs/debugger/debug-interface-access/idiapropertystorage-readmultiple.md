---
title: "IDiaPropertyStorage::ReadMultiple |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ead9e28f86067c08aa610fc902f2a0847bfb25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
指定されたプロパティの現在のセットからプロパティを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cpspec`  
 [in]指定したプロパティの数、`rgpspec`配列。 0 の場合、メソッドはプロパティを返しませんが返さ`S_OK`成功コードとして。  
  
 `rgpspec`  
 [in]読み込まれるプロパティの配列。 プロパティ ID で、または、省略可能な文字列名によって、プロパティを指定することができます。 配列内の特定の順序でプロパティを指定する必要はありません。 配列には、単純なプロパティの戻り値の重複するプロパティの値としてその結果、重複するプロパティを含めることができます。 非単純プロパティは、それらを開く、2 回目の試行でアクセスが拒否されたを返す必要があります。 配列には、プロパティの Id と文字列 Id の組み合わせを含めることができます。 この配列は以上である必要があります`cpspec`プロパティの値の数。  
  
 `rgvar`  
 [入力、出力].配列`PROPVARIANT`各プロパティの値を使用して格納する構造体 (Microsoft.VisualStudio.OLE.Interop 名前空間) にします。 配列にする必要がありますには、少なくとも`cpspec`サイズ内の要素。 呼び出し元は、配列内の値を初期化する必要はありません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合は 1 つまたは複数のプロパティが見つかりませんでした。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プロパティが見つからなかったかどうかの対応するエントリ、`rgvar`配列が含まれる、`VARIANT`の型と`VT_EMPTY`です。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)