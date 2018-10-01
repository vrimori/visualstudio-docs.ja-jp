---
title: IDiaPropertyStorage::ReadPropertyNames |Microsoft Docs
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
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f20674da015cb31747afc9cce413d3f2290b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533860"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaPropertyStorage::ReadPropertyNames](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-readpropertynames)します。  
  
対応する文字列名を取得では、プロパティの識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cpropid`  
 [in]プロパティ id の数`rgpropid`です。  
  
 `rgpropid`  
 [in]プロパティ id の名前を取得する対象の配列 (`PROPID`として WTypes.h で定義されている、 `ULONG`)。  
  
 `rglpwstrName`  
 [入力、出力]指定したプロパティ id のプロパティ名の配列。 配列のプロパティ名の要求の数を保持するために事前に割り当てる必要があり、以上を格納できる必要があります`cpropid``BSTR`文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 返されるプロパティの名前を解放する必要があります (呼び出すことによって、`SysFreeString`関数) が必要な不要になった場合。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



