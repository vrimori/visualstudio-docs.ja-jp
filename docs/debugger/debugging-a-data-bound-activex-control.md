---
title: データ連結 ActiveX コントロールのデバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df11571bb1e37d458fd647ce1524f67432617b8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474292"
---
# <a name="debugging-a-data-bound-activex-control"></a>データ連結 ActiveX コントロールのデバッグ
データ ソース コントロールに連結する ActiveX コントロールを開発している場合、独自のコンテナー アプリケーションを作成し、そのコンテナーを使用して ActiveX コントロールをデバッグできます。  
  
 たとえば、ダイアログ ベースの MFC アプリケーションを作成して、ダイアログ ボックスにデータ連結コントロールとデータ ソース コントロールを配置します。 この MFC アプリケーションは、データ連結 ActiveX コントロールをデバッグするためのコンテナー実行可能ファイルとして、ランタイム テストに使用できます。  
  
## <a name="using-the-test-container"></a>テスト コンテナーの使用  
 簡単に変更できるコンテナーでコントロールまたはコンテナーのさまざまなインターフェイスをサポートする場合は、デバッグ セッションの実行可能ファイルとして ActiveX テスト コンテナーを使用します。 ActiveX テスト コンテナーでクリックして**オプション**から、**コンテナー**  メニューのさまざまなインターフェイスを有効にします。 詳細については、次を参照してください。[プロパティのテストおよびテスト コンテナーでイベント](/cpp/mfc/testing-properties-and-events-with-test-container)です。  
  
 デバッグ中にコンテナーのコードにステップ インする必要がある場合は、デバッグ バージョンのコンテナーを使用するか、デバッグ バージョンの ActiveX テスト コンテナーを使用します。 詳細については、次を参照してください。 [TSTCON サンプル: ActiveX コントロール テスト コンテナー](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600)です。  
  
## <a name="see-also"></a>関連項目  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [ActiveX コントロール](/cpp/mfc/activex-controls)