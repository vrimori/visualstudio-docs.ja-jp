---
title: CV_access_e |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6de95d74b8d7edc3bde08437c3d018270758112
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878987"
---
# <a name="cvaccesse"></a>CV_access_e
メンバー関数と変数の可視性 (アクセス レベル) のスコープを指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elements  
 CV_private  
 メンバーは、プライベート アクセスを持ちます。  
  
 CV_protected  
 メンバーがアクセスを保護してきました。  
  
 CV_public  
 メンバーは、パブリック アクセスを持ちます。  
  
## <a name="remarks"></a>Remarks  
 `friend`アクセス指定子は含まれませんので、通常は、クラスの private と protected の両方の要素にアクセスできる非メンバー関数によって使用されます。 使用して、 [idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)でシンボルを検索するメソッド`SymTagFriend`アクセスします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)