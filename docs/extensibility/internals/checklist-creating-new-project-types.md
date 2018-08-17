---
title: 'チェックリスト: 新しいプロジェクトの種類を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69eaf52f9864b61cfc5045da9dbaf0ca6b4410b9
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511666"
---
# <a name="checklist-create-new-project-types"></a>チェックリスト: 新しいプロジェクトの種類を作成します。
新しいプロジェクトの種類を作成するいくつかのタスクを完了する必要があります。 次のチェックリストでは、これらのタスクのガイドを提供します。  
  
1.  新しいプロジェクトの種類の機能を設計します。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)します。  
  
2.  どのエディターをコード要素とその他のプロジェクト要素の使用を決定します。 コアまたは標準のエディターを使用するか作成して、プロジェクト固有のエディターを使用することができます。 詳細については、次を参照してください。[カスタム エディターとデザイナーを作成する](../../extensibility/creating-custom-editors-and-designers.md)と[方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)します。  
  
3.  プロジェクト項目を持つへの参加のレベルを決定する、**クラス ビュー**と**オブジェクト ブラウザー**します。 詳細については、次を参照してください。[シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)します。  
  
4.  プロジェクトとプロジェクト項目用に以前に行った設計上の決定に基づいて新しいクラスを派生します。  
  
5.  次のプロジェクトの種類のコンポーネントのコードを記述します。  
  
    -   新しいプロジェクトを作成して、既存のプロジェクトを開くを管理するプロジェクト ファクトリ。 詳細については、次を参照してください。[プロジェクト ファクトリを使用してプロジェクトのインスタンスを作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)です。  
  
    -   プロジェクトの階層とコマンド処理します。 詳細については、次を参照してください[プロジェクトの種類 (C++) を実装するために使用 HierUtil7 プロジェクト クラス](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)、[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)、[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)、および。[Menucommand とOleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)します。  
  
    -   プロジェクト項目の管理、プロジェクトの追加など、**新しいプロジェクト** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクトとプロジェクト項目テンプレートを追加](../../extensibility/internals/adding-project-and-project-item-templates.md)と[プロジェクトと項目テンプレートを登録](../../extensibility/internals/registering-project-and-item-templates.md)します。  
  
    -   プロジェクトの状態、および個々 のアイテムの永続化します。 詳細については、次を参照してください。[開いているプロジェクト項目を保存および](../../extensibility/internals/opening-and-saving-project-items.md)します。 解決策の情報の永続化は、次を参照してください。[ソリューション](../../extensibility/internals/solutions.md)します。  
  
    -   [プロパティ] ウィンドウに表示するプロパティを構成に依存しません。 詳細については、次を参照してください。[プロパティの拡張](../../extensibility/internals/extending-properties.md)します。  
  
    -   プロジェクト構成プロパティの構成に依存するプロパティを表示するプロパティ ページに実装されています。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)します。  
  
    -   デプロイの出力を列挙しています。 詳細については、次を参照してください。[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)します。  
  
    -   プロジェクトのスタートアップ サービス。 詳細については、次を参照してください。[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)と[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)します。  
  
    -   派生したクラスのオブジェクト、または`IDispatch`自動化のために使用できます。  
  
    -   XML コマンド テーブル (*.vsct*) ファイル。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
6.  テスト、デバッグ、およびプロジェクトの種類を開始します。  
  
7.  プロジェクトを表示、**プロジェクト**のタブ、**参照の追加** ダイアログ ボックスを設定して`VARIANT_TRUE`の値として`VSHPROPID_ShowProjInSolutionPage`します。 詳細については、<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> および <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> を参照してください。  
  
8.  Microsoft インストーラーの作成 (*.msi*)、Vspackage のインストール用のファイル。 詳細については、次を参照してください。 [Windows インストーラーによる Vspackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)、[プロジェクトの種類を登録](../../extensibility/internals/registering-a-project-type.md)、および[Vspackage](../../extensibility/internals/vspackages.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [プロジェクトの種類を作成する場合](../../extensibility/internals/when-to-create-project-types.md)   
 [プロジェクトの種類を作成します。](../../extensibility/internals/creating-project-types.md)