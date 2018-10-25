---
title: IDiaStackWalkHelper::get_registerValue |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af5f68aaf5b2caed50d28a1a53022a095d478e60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887918"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
レジスタの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `index`  
 [in]値、 [CV_HREG_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)から値を取得する登録を指定する列挙体。  
  
 `pRetVal`  
 [out]レジスタの現在の値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 サイズに関係なく、`pRetVal`パラメーター、実装がのみ何レジスタは、通常は保持を格納する必要があります。 など、8 ビット レジスタのみ、最下位 8 ビットの指定された値を保持します。 この 8 ビット値は、このメソッドから返されるときに 64 ビットに拡張されます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)