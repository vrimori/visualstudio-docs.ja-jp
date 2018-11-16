---
title: 'チェックリスト: 新しいプロジェクトの種類を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737357"
---
# <a name="checklist-creating-new-project-types"></a>チェック リスト: 新しいプロジェクト タイプの作成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

新しいプロジェクトの種類を作成するいくつかのタスクを完了する必要があります。 次のチェックリストでは、これらのタスクのガイドを提供します。  
  
1.  新しいプロジェクトの種類の機能を設計します。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)します。  
  
2.  どのエディターをコード要素とその他のプロジェクト要素の使用を決定します。 コアまたは標準のエディターを使用するか作成して、プロジェクト固有のエディターを使用することができます。 詳細については、次を参照してください。[を作成するカスタム エディターとデザイナー](../../extensibility/creating-custom-editors-and-designers.md)と[方法: 開いているプロジェクト固有のエディター](../../extensibility/how-to-open-project-specific-editors.md)します。  
  
3.  プロジェクト項目を持つへの参加のレベルを決定する、**クラス ビュー**と**オブジェクト ブラウザー**します。 詳細については、次を参照してください。[をサポートしているシンボル参照ツール](../../extensibility/internals/supporting-symbol-browsing-tools.md)します。  
  
4.  プロジェクトとプロジェクト項目用に以前に行った設計上の決定に基づいて新しいクラスを派生します。  
  
5.  次のプロジェクトの種類のコンポーネントのコードを記述します。  
  
    -   新しいプロジェクトを作成して、既存のプロジェクトを開くを管理するプロジェクト ファクトリ。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)します。  
  
    -   プロジェクトの階層とコマンド処理します。 詳細については、次を参照してください[ビルド内にありません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)、[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)、[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)。と[Menucommand とします。OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)します。  
  
    -   プロジェクト項目の管理、プロジェクトの追加など、**新しいプロジェクト** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)と[登録プロジェクトと項目テンプレート](../../extensibility/internals/registering-project-and-item-templates.md)します。  
  
    -   プロジェクトの状態、および個々 のアイテムの永続化します。 詳細については、次を参照してください。[とプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。 解決策の情報の永続化は、次を参照してください。[ソリューション](../../extensibility/internals/solutions.md)します。  
  
    -   [プロパティ] ウィンドウに表示する独立したプロパティを構成します。 詳細については、次を参照してください。[拡張プロパティ](../../extensibility/internals/extending-properties.md)します。  
  
    -   プロジェクト構成プロパティの構成に依存するプロパティを表示するプロパティ ページに実装されています。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)します。  
  
    -   デプロイの出力を列挙しています。 詳細については、次を参照してください。[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)します。  
  
    -   プロジェクトのスタートアップ サービス。 詳細については、次を参照してください。[プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)と[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)します。  
  
    -   派生したクラスのオブジェクト、または`IDispatch`自動化のために使用できます。  
  
    -   XML コマンド テーブル (.vsct) ファイル。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
6.  テスト、デバッグ、およびプロジェクトの種類を開始します。  
  
7.  プロジェクトを表示、**プロジェクト**のタブ、**参照の追加** ダイアログ ボックスを設定して`VARIANT_TRUE`の値として`VSHPROPID_ShowProjInSolutionPage`します。 詳細については、次のトピックを参照してください。 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> および <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Vspackage をインストールするための Microsoft インストーラー (.msi) ファイルを作成します。 詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)、[プロジェクトの種類を登録する](../../extensibility/internals/registering-a-project-type.md)、および[Vspackage](../../extensibility/internals/vspackages.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [プロジェクトの種類を作成する場合](../../extensibility/internals/when-to-create-project-types.md)   
 [プロジェクト タイプの作成](../../extensibility/internals/creating-project-types.md)

