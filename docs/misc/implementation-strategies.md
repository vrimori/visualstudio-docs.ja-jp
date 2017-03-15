---
title: "実装戦略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage、実装戦略"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 実装戦略
自動化アドイン、Vspackage、Managed Extensibility Framework \(MEF\) コンポーネント パーツ、またはこれら 3 つの組み合わせを使用して Visual Studio を拡張することができます。 一般に、アドインは開発が容易ですが、VSPackage または MEF コンポーネント パーツに比べて性能が劣ります。 アドインは機能拡張インターフェイスを呼び出すことが可能で、VSPackage と MEF コンポーネント パーツは Visual Studio 自動化モデルを利用できます。 いくつかの異なる手法を組み合わせて、効果的なソリューションを作成できます。  
  
 VSPackage は、アンマネージ コードまたはマネージ コードで記述できます。 新しい Vspackage は、マネージ パッケージ フレームワーク \(MPF\) を使用して、マネージ コードで作成することをお勧めします。 アンマネージ コードで作成可能なほぼすべてが、簡単かつ安全にマネージ コードで実装できます。 ただし、アンマネージ コードで記述されたレガシ アプリケーションは引き続き Visual Studio で動作します。  
  
 簡単な拡張によって、ツール ウィンドウを追加したり、ステータス バーまたは出力ウィンドウといった Visual Studio の UI 要素に情報を送信したりすることが可能です。 より複雑なアプリケーションは、サーバー エクスプローラーなどの Visual Studio の階層として記述することができます。 プロジェクト、エディター、またはデザイナーを実装することによってさらに強力にすることもできます。 たとえば、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] と [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 自体が言語サービスとして実装されています。  
  
## 関連項目  
 [Visual Studio SDK と自動化](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 自動化、VSpackage、またはその組み合わせを使用した、Visual Studio 機能拡張アプリケーションの作成について説明します。  
  
 [Visual Studio SDK とマネージ コード](/visual-cpp/misc/visual-studio-sdk-and-managed-code)  
 VSPackage をマネージ コードで記述するさまざまな方法を比較します。  
  
 [Visual Studio IDE の概念](/visual-cpp/misc/visual-studio-ide-concepts)  
 VSpackage とサービスを使用する方法の基本について説明します。  
  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)  
 状態ウィンドウと出力ウィンドウなど、Visual Studio での共通の UI アプリケーション要素について説明します。  
  
 [Visual Studio での階層](../extensibility/internals/hierarchies-in-visual-studio.md)  
 ノードのツリーとして統合開発環境 \(IDE\) で表示される Visual Studio の階層の概要を示します。  
  
 [プロジェクト](../extensibility/internals/projects.md)  
 プロジェクトとソリューションのクラスの概要を示します。  
  
 [エディターと言語サービスの拡張機能](../extensibility/editor-and-language-service-extensions.md)  
 コードおよびテキスト エディターを拡張する方法と、カスタム エディターおよびデザイナーを作成する方法を示します。  
  
 [従来の言語サービスの拡張機能](../extensibility/internals/legacy-language-service-extensibility.md)  
 言語サービスを作成する方法を示します。  
  
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)  
 VSSDK のリファレンス ドキュメント。  
  
## 参照  
 [Visual Studio 拡張機能の開発を始めました](../extensibility/starting-to-develop-visual-studio-extensions.md)