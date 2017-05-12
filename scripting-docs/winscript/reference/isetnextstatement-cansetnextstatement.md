---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
このメソッドは、実行されるコードの次のステートメントを決定します。指定した位置までの実行ポイントが設定できるかどうかを判定します。  
  
## 構文  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### パラメーター  
 `pStackFrame`  
 \[出力\]スタック フレーム オブジェクトへのポインター。  
  
 `pCodeContext`  
 \[入力\]コード コンテキスト オブジェクトへのポインター。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|次のコード ステートメントは、指定したコンテキストに更新できます。|  
|`S_FALSE`|次のコード ステートメントは、指定したコンテキストに更新できません。|  
  
## 解説  
  
## 参照  
 [ISetNextStatement インターフェイス](../../winscript/reference/isetnextstatement-interface.md)