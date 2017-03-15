---
title: "チェックリスト: 新しいプロジェクトの種類を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] の新しい種類の作成"
  - "プロジェクトの種類を作成するためのチェックリスト"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# チェックリスト: 新しいプロジェクトの種類を作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新しいプロジェクトの種類を作成するいくつかのタスクを完了する必要があります。 次のチェックリストは、それらのタスクにガイドを提供します。  
  
1.  新しいプロジェクトの種類の機能を設計します。 詳細については、「[プロジェクトの種類のデザインの決定](../../extensibility/internals/project-type-design-decisions.md)」を参照してください。  
  
2.  どのエディターをコード要素およびその他のプロジェクト要素の使用を決定します。 コアまたは標準のエディターを使用する、または作成して、プロジェクト固有のエディターを使用することができます。 詳細については、次のトピックを参照してください。[カスタム エディターとデザイナーを作成します。](../../extensibility/creating-custom-editors-and-designers.md) および[方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  プロジェクト項目は参加レベルを決定する、 **クラス ビュー** と **オブジェクト ブラウザー**します。 詳細については、「[シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)」を参照してください。  
  
4.  プロジェクトとプロジェクト項目に対して以前に作成した設計上の決定に基づいて新しいクラスを派生します。  
  
5.  次のプロジェクトの種類のコンポーネントのコードを記述します。  
  
    -   新しいプロジェクトを作成して既存のプロジェクトを開くことを管理するプロジェクト ファクトリ。 詳細については、「[プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)」を参照してください。  
  
    -   プロジェクトの階層とコマンド処理します。 詳細については、次を参照してください。 [ビルドに存在しません: プロジェクトの種類 \(C\+\+\) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/ja-jp/a5c16a09-94a2-46ef-87b5-35b815e2f346), 、[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md), 、[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md) と [MenuCommand と  OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)です。  
  
    -   プロジェクト項目の管理、プロジェクトの追加など、 **新しいプロジェクト** \] ダイアログ ボックス。 詳細については、次のトピックを参照してください。[プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md) および[プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   プロジェクトの状態および個々 のアイテムの永続化します。 詳細については、「[開く、プロジェクト項目を保存します。](../../extensibility/internals/opening-and-saving-project-items.md)」を参照してください。 解決策の情報の永続化は、次を参照してください。 [ソリューション](../../extensibility/internals/solutions.md)します。  
  
    -   \[プロパティ\] ウィンドウに表示する独立したプロパティを構成します。 詳細については、「[プロパティを拡張します。](../../extensibility/internals/extending-properties.md)」を参照してください。  
  
    -   プロジェクト構成プロパティの構成に依存するプロパティを表示するプロパティ ページに実装されています。 詳細については、「[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)」を参照してください。  
  
    -   展開の出力を列挙しています。 詳細については、「[出力のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)」を参照してください。  
  
    -   プロジェクトのスタートアップ サービスです。 詳細については、[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md) および [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md) を参照してください。  
  
    -   オブジェクト、またはクラスから派生した `IDispatch`, は、自動化のために利用できます。  
  
    -   XML コマンド テーブル \(.vsct\) ファイル。 詳細については、「[Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
6.  テスト、デバッグ、およびプロジェクトの種類を開始します。  
  
7.  プロジェクトを表示、 **プロジェクト** のタブ、 **参照の追加** \] ダイアログ ボックスを設定して `VARIANT_TRUE` の値として `VSHPROPID_ShowProjInSolutionPage`します。 詳細については、次のトピックを参照してください。<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> および<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Vspackage をインストールするための Microsoft インストーラー \(.msi\) ファイルを作成します。 詳細については、「[Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)「[プロジェクトの種類を登録します。](../../extensibility/internals/registering-a-project-type.md)および「[Vspackages にあります。](../../extensibility/internals/vspackages.md)」を参照してください。  
  
## 参照  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [プロジェクトの種類を作成する場合](../../extensibility/internals/when-to-create-project-types.md)   
 [プロジェクトの種類を作成します。](../../extensibility/internals/creating-project-types.md)