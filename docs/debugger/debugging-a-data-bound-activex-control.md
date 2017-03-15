---
title: "データ連結 ActiveX コントロールのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ActiveX コントロール, デバッグ"
  - "コントロール [Visual Studio], ActiveX"
  - "データ バインド コントロール, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# データ連結 ActiveX コントロールのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

データ ソース コントロールに連結する ActiveX コントロールを開発している場合、独自のコンテナー アプリケーションを作成し、そのコンテナーを使用して ActiveX コントロールをデバッグできます。  
  
 たとえば、ダイアログ ベースの MFC アプリケーションを作成して、ダイアログ ボックスにデータ連結コントロールとデータ ソース コントロールを配置します。  この MFC アプリケーションは、データ連結 ActiveX コントロールをデバッグするためのコンテナー実行可能ファイルとして、ランタイム テストに使用できます。  
  
## テスト コンテナーの使用  
 簡単に変更できるコンテナーでコントロールまたはコンテナーのさまざまなインターフェイスをサポートする場合は、デバッグ セッションの実行可能ファイルとして ActiveX テスト コンテナーを使用します。  ActiveX テスト コンテナーで、**\[コンテナー\]** メニューの **\[オプション\]** をクリックしてさまざまなインターフェイスを有効にします。  詳細については、「[テスト コンテナーでのプロパティとイベントのテスト](/visual-cpp/mfc/testing-properties-and-events-with-test-container)」を参照してください。  
  
 デバッグ中にコンテナーのコードにステップ インする必要がある場合は、デバッグ バージョンのコンテナーを使用するか、デバッグ バージョンの ActiveX テスト コンテナーを使用します。  詳細については、「[TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/ja-jp/72fa40ef-27d3-400c-813f-10b03236e600)」を参照してください。  
  
## 参照  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [ActiveX コントロール](/visual-cpp/mfc/activex-controls)