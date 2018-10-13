---
title: ドメイン固有言語ツールの概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c0c8730d2a73b5e6dd2c48138c1633e24234db29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273261"
---
# <a name="overview-of-domain-specific-language-tools"></a>ドメイン固有言語ツールの概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドメイン固有言語ツール (DSL ツール) でホストされている[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、ドメイン固有言語を設計および言語に基づくモデルを作成するユーザーが必要なすべてのものを生成します。  
  
 DSL ツールでは、次のツールが含まれています。  
  
-   別のソリューション テンプレートを使用して、ドメイン固有言語の開発を始めるのに役立つプロジェクト ウィザード。  
  
-   デザイナーの作成と、ドメイン固有言語定義を編集します。  
  
-   ドメイン固有言語定義が整形式し、問題がある場合は、エラーと警告を表示することを確認する検証エンジン。  
  
-   入力としてドメイン固有言語定義を受け取り、出力としてのソース コードを生成するコード ジェネレーター。  
  
## <a name="the-dsl-tools-solution"></a>DSL ツール ソリューション  
 ドメイン固有のデザイナーのウィザードには、次のソリューション テンプレートが用意されています。  
  
-   タスク フロー  
  
-   クラス ダイアグラム  
  
-   最小言語  
  
-   コンポーネント モデル  
  
-   最小限の WPF  
  
-   最小 Windows.Forms  
  
-   DSL ライブラリ  
  
 詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)します。  
  
 ウィザードを作成、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]次のプロジェクトを含むソリューション。  
  
-   Dsl  
  
     Dsl プロジェクトでは、ドメイン固有言語と、編集、および処理ツールを定義します。  
  
-   **DslPackage**  
  
     DslPackage プロジェクトは、言語ツール統合する方法を決定します。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
## <a name="the-dsl-tools-graphical-interface"></a>DSL ツールのグラフィカル インターフェイス  
 DSL ツールのグラフィカル インターフェイスを使用して、ドメイン固有言語に要素および関係を追加することができます。 要素を追加した後は、図形にマップの色のカスタマイズ、デコレータを追加してその外観を定義できます。 ツールボックスに要素を追加することもできます。  
  
## <a name="validation-in-dsl-tools"></a>DSL ツールでの検証  
 Dsl は、ドメイン モデルがコード生成のための基本的な要件を満たしているかどうかを確認する検証の 1 つのレベルを提供します。 通常、独自のドメイン固有言語を作成するときに、ビジネス ロジック ルールを表現する独自の検証を追加します。 カスタム検証の詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。  
  
 設計する際に多くの場合、ドメイン固有言語を検証することをお勧めします。 ドメイン固有言語には、検証エラーが発生した場合は、ソース コードを生成できません。 クリックして、テンプレートからソース コードを生成するプロセスが実行される**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。 言語の定義を変更するたびにも必ず**すべてのテンプレートの変換**します。 詳細については、次を参照してください。[方法: ドメイン固有言語ソリューションを作成](../modeling/how-to-create-a-domain-specific-language-solution.md)です。  
  
## <a name="customization-of-dsl-tools"></a>DSL ツールのカスタマイズ  
 お使いの言語で制約を定義するために、追加のコードをモデルの動作を設定し直すを行うことができます。 必要な場合は、テキスト テンプレートを変更することで大幅な変更を行うことができます。  
  
## <a name="distributing-your-dsl-solution"></a>DSL ソリューションを配布します。  
 DSL ツールでホストされているパッケージを生成する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 パッケージには、ツールボックス、DSL エクスプ ローラーでは、およびその他のユーザー、ドメイン固有言語を使用してモデルを作成できるようにする UI 要素が表示されます。  
  
 ビルドおよびで DSL Tools のソリューションを実行する場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、2 番目のインスタンスの[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]言語のユーザーに、ドメイン固有言語の表示方法を示しています。 配布することがすべてが正常に動作することを確認した後、`.vsix`ファイルを DslPackage プロジェクトのビルド フォルダーに表示されます。 このファイルは、として DSL をインストールするために使用できます、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]他のコンピューター上の拡張機能。  詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)します。  
  
## <a name="see-also"></a>関連項目  
 [実験用インスタンス](../extensibility/the-experimental-instance.md)   
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



