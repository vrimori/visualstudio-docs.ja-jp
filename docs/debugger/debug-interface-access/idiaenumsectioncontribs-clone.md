---
title: Idiaenumsectioncontribs::clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Clone method
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89c5c7eef010de75165ac6d28e0690fe2e906d00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999159"
---
# <a name="idiaenumsectioncontribsclone"></a>IDiaEnumSectionContribs::Clone
現在の列挙子と同じ列挙状態を格納する列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Clone(   
   IDiaEnumSectionContrib** ppenum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 ppenum  
 [out]返します、 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)列挙子の重複を含むオブジェクト。 列挙子のみの投稿物がないセクションが重複しています。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)