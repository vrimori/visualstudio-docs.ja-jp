---
title: NameSearchOptions |Microsoft Docs
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
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17896f1a32ab939a7f2ee5a2ebd863136ea5aaa1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771343"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

シンボルとファイル名の検索オプションを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elements  
 `nsNone`  
 オプションは指定されていません。  
  
 `nsfCaseSensitive`  
 大文字小文字を区別する名前の一致を適用します。  
  
 `nsfCaseInsensitive`  
 大文字の名前の一致を適用します。  
  
 `nsfFNameExt`  
 パスと名前を処理し、.ext という名前の一致を適用します。  
  
 `nsfRegularExpression`  
 ワイルドカードとしてアスタリスク (*) や疑問符 (?) を使用して区別する名前の一致を適用します。  
  
 `nsfUndecoratedName`  
 装飾されていないし、装飾名がシンボルにのみ適用されます。  
  
## <a name="remarks"></a>Remarks  
 この列挙の値は、次のメソッドに渡されます。  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: dia2.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession::findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



