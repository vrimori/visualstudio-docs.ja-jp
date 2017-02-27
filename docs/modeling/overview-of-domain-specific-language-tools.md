---
title: "ドメイン固有言語ツールの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 54
---
# ドメイン固有言語ツールの概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユーザーは言語に基づいてモデルを作成[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]するために必要となるホスト ドメイン固有言語をデザインしすべてを生成できるツール ドメイン固有言語 （DSL ツール）。  
  
 次のツールはDSL ツールに含まれています :  
  
-   役立つ複数のソリューション テンプレートを使用してプロジェクト ウィザード ドメイン固有言語の開発を開始します。  
  
-   ドメイン固有言語定義を作成および編集するためのグラフィカル デザイナー。  
  
-   ドメイン固有言語定義が正しい形式であることを検証するエンジンは問題が発生した場合エラーと警告が表示されます。  
  
-   入力としてドメイン固有言語定義を受け取り出力としてソース・コードを生成するコード ジェネレーター。  
  
## DSL ツールのソリューションには  
 デザイナーのドメイン固有のウィザードは次のソリューション テンプレートが用意されています :  
  
-   タスクのフロー  
  
-   クラス ダイアグラム  
  
-   最小限の言語  
  
-   構成モデル  
  
-   最小限の WPF  
  
-   最小 Windows.Forms  
  
-   DSL ライブラリ  
  
 詳細については、「[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)」を参照してください。  
  
 このウィザードでは次の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトを含むソリューションを作成します :  
  
-   Dsl  
  
     Dsl プロジェクトはドメイン固有言語および編集し処理ツールを定義します。  
  
-   **DslPackage**  
  
     DslPackage プロジェクトは言語ツールが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] との統合方法を決定します。  
  
## DSL はグラフィカル インターフェイスに Tools  
 ドメイン固有言語の要素および関係を追加するにはDSL ツールのグラフィカル インターフェイスを使用できます。  要素を追加した後図形に割り当てること色定義をカスタマイズしデコレータを追加すると外観を指定できます。  またツールボックスに要素を追加します。  
  
## DSL ツールの検証  
 Dsl はドメイン モデルがコードを生成するための基本的な要件を満たしていることを確認する検証の 1 レベルを示します。  通常独自のドメイン固有言語を作成する場合はビジネス ロジック ルールを表現する独自の検証を追加します。  カスタム検証の詳細については[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md) を参照してください。  
  
 これはデザイン時にドメイン固有言語を頻繁に検証することをお勧めします。  ドメイン固有言語に検証エラーがある場合ソース・コードを生成できません。  テンプレートからソース・コードを生成するプロセスはソリューション エクスプローラーのツール バーの \[ENT0ENT\] をクリックして行われます。  言語定義を変更するたびに **すべてのテンプレートの変換 \(&T\)** があります。  詳細については、「[方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)」を参照してください。  
  
## DSL ツールのカスタマイズ  
 モデルの動作を調整し言語上の制約を定義する追加のコードを記述できます。  必要に応じてテキスト テンプレートの変更によって重要な変更を加えることができます。  
  
## DSL のソリューションの配置  
 DSL ツールは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でホスティングパッケージを生成します。  パッケージはツールボックスDSL のエクスプローラーおよびユーザーがドメイン固有言語を使用してモデルを作成できる他の UI 要素を表示します。  
  
 DSL を示して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のソリューションをビルドして実行し[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の 2 番目のインスタンスはドメイン固有言語の言語のユーザーにどのように表示されるかを示します。  すべてが正しく動作することを確認したらDslPackage プロジェクトのビルド フォルダーにある `.vsix` ファイルを配布できます。  このファイルには他のコンピューターの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の拡張として DSL のインストールに使用できます。  詳細については、「[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)」を参照してください。  
  
## 参照  
 [実験用インスタンス](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)