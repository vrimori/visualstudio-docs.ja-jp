---
title: "ScriptEngineMajorVersion 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>ScriptEngineMajorVersion 関数 (JavaScript)
使用されているスクリプト エンジンのメジャー バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>コメント  
 返り値は、使用されているスクリプト言語のダイナミック リンク ライブラリ (DLL) に含まれているバージョン情報に直接対応しています。  
  
## <a name="example"></a>例  
 `ScriptEngineMajorVersion` 関数の使用例を次に示します。  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ScriptEngine 関数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 関数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion 関数](../../javascript/reference/scriptengineminorversion-function-javascript.md)