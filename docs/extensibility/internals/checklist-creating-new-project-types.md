---
title: "チェックリスト: 新しいプロジェクトの種類を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ea9c2ebd295fe463192c50da402240e0b1df1304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="checklist-creating-new-project-types"></a>チェックリスト: 新しいプロジェクトの種類を作成します。
新しいプロジェクトの種類を作成するいくつかのタスクを完了する必要があります。 次のチェックリストでは、それらのタスクにガイドを提供します。  
  
1.  新しいプロジェクトの種類の機能を設計します。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)です。  
  
2.  どのエディターをコードおよびその他のプロジェクト要素の使用を決定します。 コアまたは標準のエディターを使用することができますか作成して、プロジェクト固有のエディターを使用することができます。 詳細については、次を参照してください。[を作成するカスタム エディターやデザイナー](../../extensibility/creating-custom-editors-and-designers.md)と[する方法: 開いているプロジェクトに固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)です。  
  
3.  プロジェクト項目には参加レベルを決定する、**クラス ビュー**と**オブジェクト ブラウザー**です。 詳細については、次を参照してください。[をサポートするシンボル閲覧ツール](../../extensibility/internals/supporting-symbol-browsing-tools.md)です。  
  
4.  プロジェクトとプロジェクト項目の以前に行った設計に関する決定事項に基づいて新しいクラスを派生します。  
  
5.  次のプロジェクトの種類のコンポーネントのコードを記述します。  
  
    -   新しいプロジェクトの作成と既存のプロジェクトを開くを管理するプロジェクト ファクトリ。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)です。  
  
    -   プロジェクトの階層とコマンドの処理です。 詳細については、次を参照してください[ビルド内にありません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)、[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)、[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)。と[Menucommand とします。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)です。  
  
    -   プロジェクト アイテムの管理、プロジェクトを追加するなど、**新しいプロジェクト** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)と[を登録するプロジェクトと項目テンプレート](../../extensibility/internals/registering-project-and-item-templates.md)です。  
  
    -   プロジェクトの状態と個々 の項目の永続化します。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)です。 解決策の情報の永続化は、次を参照してください。[ソリューション](../../extensibility/internals/solutions.md)です。  
  
    -   [プロパティ] ウィンドウに表示する独立したプロパティを構成します。 詳細については、次を参照してください。[の拡張プロパティ](../../extensibility/internals/extending-properties.md)です。  
  
    -   プロジェクト構成プロパティの構成に依存するプロパティを表示するプロパティ ページに実装されています。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)です。  
  
    -   展開の出力を列挙しています。 詳細については、次を参照してください。[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)です。  
  
    -   プロジェクトのスタートアップ サービス。 詳細については、次を参照してください。[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)と[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)です。  
  
    -   オブジェクト、またはクラスから派生した`IDispatch`は、自動化に利用できます。  
  
    -   XML コマンド テーブル (.vsct) ファイル。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)です。  
  
6.  テスト、デバッグ、およびプロジェクトの種類を開始します。  
  
7.  プロジェクトを表示、**プロジェクト**のタブ、**参照の追加** ダイアログ ボックスを設定して`VARIANT_TRUE`の値として`VSHPROPID_ShowProjInSolutionPage`です。 詳細については、<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> および <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> を参照してください。  
  
8.  Vspackage をインストールするための Microsoft インストーラー (.msi) ファイルを作成します。 詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)、 [、プロジェクトの種類を登録する](../../extensibility/internals/registering-a-project-type.md)、および[Vspackage](../../extensibility/internals/vspackages.md)です。  
  
## <a name="see-also"></a>参照  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [プロジェクトの種類を作成する場合](../../extensibility/internals/when-to-create-project-types.md)   
 [プロジェクト タイプの作成](../../extensibility/internals/creating-project-types.md)