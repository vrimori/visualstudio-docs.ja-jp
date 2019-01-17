---
title: JS_PROPERTY_MEMBERS 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57d933a86d5ffe8d2b8aec243b5eb6bd2ae93a59
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096831"
---
# <a name="jspropertymembers-enumeration"></a>JS_PROPERTY_MEMBERS 列挙型
オブジェクトのメンバーの要求で返される情報の種類を指定するフラグ。  
  
## <a name="syntax"></a>構文  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|名前|説明|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|すべてのメンバーを列挙する要求を表します。|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|引数だけを列挙する要求を表します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)