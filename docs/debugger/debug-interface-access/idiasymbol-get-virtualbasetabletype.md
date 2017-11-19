---
title: "Idiasymbol::get_virtualbasetabletype |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcbc4478830a730f684b008c88ff5c6490a1c596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
仮想ベース テーブルへのポインターの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`pRetVal`|[out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)ベース テーブルの種類を指定するオブジェクト。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
 仮想ベース テーブルへのポインター (`vbtptr`) 非表示を指すポインター、 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable が仮想基底クラスからの継承を処理します。 A`vbtptr`継承されたクラスに応じて異なるサイズを持つことができます。  
  
 このメソッドが戻る、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) vbtptr のサイズを決定するために使用できるオブジェクト。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)