---
title: Idiasymbol::get_virtualbasetabletype |Microsoft Docs
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
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13dd25c60e373ea747ec802999ce998271ff3e8f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536330"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiasymbol::get_virtualbasetabletype](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype)します。  
  
仮想ベース テーブルのポインターの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`pRetVal`|[out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)ベース テーブルの種類を指定するオブジェクト。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 仮想ベース テーブルのポインター (`vbtptr`) 非表示を指すポインター、 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vtable 仮想基底クラスからの継承を処理します。 A`vbtptr`継承されたクラスによって異なるサイズであることができます。  
  
 このメソッドが戻る、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) vbtptr のサイズを決定するために使用できるオブジェクト。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



