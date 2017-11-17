---
title: "ScriptEngineBuildVersion 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginebuildversion-function-javascript"></a>ScriptEngineBuildVersion 関数 (JavaScript)
使用されているスクリプト エンジンのビルド バージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>コメント  
 返り値は、使用されているスクリプト言語のダイナミック リンク ライブラリ (DLL) に含まれているバージョン情報に直接対応しています。  
  
## <a name="example"></a>例  
 `ScriptEngineBuildVersion` 関数の使用例を次に示します。  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ScriptEngine 関数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion 関数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion 関数](../../javascript/reference/scriptengineminorversion-function-javascript.md)