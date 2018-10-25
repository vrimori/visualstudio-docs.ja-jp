---
title: DataKind |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f2b46e420db8addf19ef8694112058bdb8b2f91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867625"
---
# <a name="datakind"></a>DataKind
データ値の特定のスコープを示します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elements  
 DataIsUnknown  
 データ シンボルを特定できません。  
  
 DataIsLocal  
 データ項目は、ローカル変数です。  
  
 DataIsStaticLocal  
 データ項目は、静的ローカル変数です。  
  
 DataIsParam  
 データ項目は、正式なパラメーターです。  
  
 DataIsObjectPtr  
 データ項目はオブジェクト ポインター (`this`)。  
  
 DataIsFileStatic  
 データ項目は、ファイル スコープ変数です。  
  
 DataIsGlobal  
 データ項目は、グローバル変数です。  
  
 DataIsMember  
 データ項目は、オブジェクト メンバー変数です。  
  
 DataIsStaticMember  
 データ項目は、クラスの静的変数です。  
  
 DataIsConstant  
 データ項目は、定数値です。  
  
## <a name="remarks"></a>Remarks  
 この列挙体の値がによって返される、 [idiasymbol::get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)