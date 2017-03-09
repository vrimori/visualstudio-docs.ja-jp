---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グラフィックス情報をアクティブにキャプチャしてグラフィックス ログ ファイルに記録するように、グラフィックス診断のアプリ内コンポーネントを準備します。  
  
## 構文  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### パラメーター  
 `vsgLogGetter`  
 パラメーターとして、`wchar_t` で構成されるバッファーの長さとそのバッファーへのポインターを受け取り、`void` を返す、呼び出し可能なエンティティ \(関数、関数ポインター、ラムダ、関数オブジェクトなど\)。  呼び出されると、呼び出し可能なエンティティは、グラフィックス情報を記録するために使用されるファイル名を決定し、返される前に指定されたバッファーにファイル名を書き込みます。  
  
## 解説  
 コンストラクターの `bDefaultInit` パラメーターを `true` に指定することで、`VsgDbg` クラスのインスタンスが構築されると `Init` 関数が自動的に呼び出されます。それ以外の場合は、グラフィックス情報をアクティブにキャプチャして記録する前に、`Init` を明示的に呼び出す必要があります。  
  
 `UnInit` を呼び出してアクティブなグラフィックス ログ ファイルを終了して閉じ、`Init` を再度呼び出して、グラフィックス情報をさらにキャプチャして新しいグラフィック ログ ファイルに記録することができます。  この操作を何度でも繰り返して、同じ `VsgDbg` インスタンスを使用して複数の独立したグラフィックス ログ ファイルを作成することができます。  
  
## 参照  
 [UnInit](../debugger/init.md)