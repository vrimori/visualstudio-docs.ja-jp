---
title: IDiaPropertyStorage::ReadPropertyNames |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d51eaed785932703a5eb97714be8dc7b407fc81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891818"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
対応する文字列名を取得では、プロパティの識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
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