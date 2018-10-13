---
title: IDiaPropertyStorage::ReadMultiple |Microsoft Docs
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
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ebfe7825dbf4690246d6a7fc2e67a84c850a96
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230816"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定された、現在のプロパティ セットからのプロパティを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cpspec`  
 [in]指定したプロパティの数、`rgpspec`配列。 0 の場合、メソッドはプロパティは返されませんが、返すは`S_OK`成功コードとして。  
  
 `rgpspec`  
 [in]プロパティの読み取りの配列。 プロパティ ID、または、省略可能な文字列名のいずれかのプロパティを指定できます。 配列内の特定の順序でプロパティを指定する必要はありません。 配列は、単純なプロパティの戻り値の重複したプロパティ値の重複するプロパティを含めることができます。 2 回目に開こうとしてでアクセスが拒否される非単純プロパティが返す必要があります。 配列は、プロパティの Id と文字列 Id の組み合わせを含めることができます。 この配列は以上である必要があります`cpspec`プロパティ値の数。  
  
 `rgvar`  
 [入力、出力]配列の`PROPVARIANT`(Microsoft.VisualStudio.OLE.Interop 名前空間の) 内の各プロパティの値を格納する構造体します。 配列は以上である必要があります`cpspec`サイズ内の要素。 呼び出し元は、配列内の値を初期化する必要はありません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`1 つまたは複数のプロパティが見つからなかった場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 かどうか、プロパティが見つかりません、対応するエントリに、`rgvar`配列に含まれる、`VARIANT`の型と`VT_EMPTY`します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



