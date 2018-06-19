---
title: ScriptEngineMinorVersion 関数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639542"
---
# <a name="scriptengineminorversion-function-javascript"></a>ScriptEngineMinorVersion 関数 (JavaScript)
使用されているスクリプト エンジンのマイナー バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>コメント  
 返り値は、使用されているスクリプト言語のダイナミック リンク ライブラリ (DLL) に含まれているバージョン情報に直接対応しています。  
  
## <a name="example"></a>例  
 `ScriptEngineMinorVersion` 関数の使用例を次に示します。  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ScriptEngine 関数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 関数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion 関数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)