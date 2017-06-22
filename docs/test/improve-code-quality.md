---
title: "コードの品質向上"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: fbc3a182d2c3dbceaa17685f649ea73a3e73ed85
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# <a name="improve-code-quality"></a>コードの品質向上
コードの品質とは何でしょう。 優れたコードの作成には、正確性、保守性、さらに簡潔さのすべてが関係しています。 コードの品質をどのように定義したとしても、Visual Studio のテスト ツールを使用することで、あなたとあなたのチームは高水準の優れたコードを開発して維持することができます。  
  
 **Requirements**  
  
-   このセクションで説明するツールおよび機能の一部は、すべての Visual Studio ではなく、特定のエディションの Visual Studio でのみ使用できます。 特定のエディション要件は、それらのツールおよび機能のドキュメントに示しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次の表に、一般的なタスクの説明と、それらのタスクを正常に完了する方法を詳しく載せたリンクを示します。  
  
|||  
|-|-|  
|[コードの単体テスト](../test/unit-test-your-code.md)|テスト エクスプローラーを使用すると、開発の手法において単体テストを容易に統合できるようになります。 Microsoft 単体テスト フレームワークまたは複数のサードパーティ フレームワークやオープン ソース フレームワークの 1 つを使用できます。|  
|[Visual Studio での Live Unit Testing](../test/live-unit-testing.md)|Live Unit Testing は、バックグラウンドで自動的に単体テストを実行し、Visual Studio のコード エディターにコード カバレッジとテスト結果をグラフィカルに表示します。|  
|[アプリケーション品質の分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|スタティック コード分析ツールは、C++ とマネージ コードにおける設計、使用方法、およびスタイルの問題を検出します。 これらの問題の多くは、標準のテスト環境では再現するのが困難なバグにつながる可能性があります。|  
|[マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|コード メトリックスとは、開発者が開発中のコードをより理解できるようにする、ソフトウェアの一連の基準です。 このメトリックスには、関数とクラスの保守容易性指数、関数のサイクロマティック複雑度、クラスの継承の深さ、およびクラス間の結合の度合いが含まれます。|  
  
## <a name="related-scenarios"></a>関連するシナリオ  
 [アプリケーション ライフサイクル管理のための Visual Studio および Team Foundation Server の導入](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 Visual Studio Team Foundation の使用経験がない場合は、チームの開発環境で使用して、アプリケーションの開発に関連する生産性を向上し、リスクを軽減する方法を学ぶことができます。  
  
 [アーキテクチャの分析およびモデリング](../modeling/analyze-and-model-your-architecture.md)  
 [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] を使用すると、ソフトウェアの設計における課題と複雑さを管理できます。 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] を使用して、現在のアプリケーションの状態および将来のアプリケーションの状態を視覚的にモデル化できます。 アプリケーションの論理的なモデルを視覚化できるダイアグラムを作成および管理すると同時に、それらを物理的なモデルに対応付けることができます。これにより、"設計中" のソフトウェアを変更、検証、および分析できます。  
  
 [アプリケーションのテスト](https://www.visualstudio.com/docs/test/overview)  
 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] および [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] を使用すると、テストのライフ サイクル全体の生産性を向上させることができます。 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] または [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] では、テスト作業の計画を作成できます。 手動テストと自動テストの両方を作成、管理、編集、および実行できます。 また、計画に基づいてテストの進行状況もレビューできます。  
  
 [PreEmptive 保護によるアプリケーションの保護 - Dotfuscator](../ide/dotfuscator/index.md)  
 Dotfuscator コミュニティ エディションを利用し、企業秘密やその他の知的財産 (IP) を守り、違法コピーや偽造を減らし、改ざんと権限のないデバッグを防止できます。  Dotfuscator はコンパイル済みのアセンブリを保護および強化します。追加のプログラミングやソース コードへのアクセスは不要です。
  
 [アプリケーションのビルド](https://www.visualstudio.com/docs/build/overview)  
 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)]を使用すると、コードの自動的なビルドを作成および管理できます。 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)]では、ドロップ サーバーを作成してビルドを配置できます。 さらに、ビルドの傾向を分析できます。  
  
 [Visual Studio Online または Team Foundation Server を使用した作業の追跡](https://www.visualstudio.com/docs/work/overview)  
 [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] を使用すると、プロジェクトの計画を作成し、これらのプロセスでアジャイル プロセス、フォーマル プロセス、またはそのバリエーションを使用しているかどうかを追跡できます。 プロジェクト計画の作成、その計画に対する進行状況の追跡、および必要な調整を行うことにより、リスクを軽減し、意図しない問題の発生を防ぎ、プロジェクトの費用を管理できます。

