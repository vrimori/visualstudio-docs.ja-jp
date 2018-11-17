---
title: SccGetVersion 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16a21ab75c8390f0bb5ff5f016f2bf5b8d04c3a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779087"
---
# <a name="sccgetversion-function"></a>SccGetVersion 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理プラグインでサポートされているソース管理プラグイン API のバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 A`LONG`サポートされているソース管理プラグイン API のバージョン番号を含むデータ型。  
  
|WORD|説明|  
|----------|-----------------|  
|HIWORD|メジャー バージョン|  
|LOWORD マクロ|マイナー バージョン|  
  
## <a name="remarks"></a>Remarks  
 ソース管理プラグインは、ソース管理プラグイン API のバージョン 1.3 をサポートする場合など、この関数では、0x0103 に返します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)

