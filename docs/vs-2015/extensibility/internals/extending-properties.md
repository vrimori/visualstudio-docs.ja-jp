---
title: プロパティの拡張 |Microsoft Docs
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
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 919b5a08f003d6e6c320edef4c1321af35f17388
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777878"
---
# <a name="extending-properties"></a>プロパティの拡張
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **プロパティ**ウィンドウはすべてサポートしています、COM と COM + コンポーネントのユニバーサル プロパティ ブラウザーを[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]製品です。 **プロパティ**ウィンドウは`ITypeInfo`情報および COM + 統合開発環境 (IDE) でその他のウィンドウで現在選択されているオブジェクトのデザイン時プロパティの一覧にメタデータを入力します。  
  
 **プロパティ**ウィンドウでは、キーボード、f4 キーを押すか、選択して開くことができますが、**プロパティ ウィンドウ**上、**ビュー**を表示および編集 メニューを使用構成に依存しない、デザイン時のプロパティと選択したオブジェクトのイベント。 ソリューションやプロジェクトの関連付けの構成に依存するプロパティに表示される[プロパティ ページ](../../extensibility/internals/property-pages.md)します。 詳細については、次を参照してください。 [NIB: プロジェクト プロパティ](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)、[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)、および[プロジェクトにおける NIB: 項目の管理](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)します。  
  
 ![プロパティ ウィンドウの概要](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
[プロパティ] ウィンドウ  
  
 このセクションの個々 の領域に関連する詳細な情報を提供する、**プロパティ**ウィンドウと、ウィンドウの設定への呼び出し、インターフェイスを実装する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロパティ ウィンドウの概要](../../extensibility/internals/properties-window-overview.md)  
 目的について説明します、**プロパティ**ツール ウィンドウとドキュメント ウィンドウのウィンドウ。  
  
 [テンプレート ポリシーとプロパティ ウィンドウ](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 エンタープライズ テンプレート プロジェクトで、プロジェクトが含まれている方法と、そのエンタープライズ テンプレート プロジェクトがポリシーを適用する方法について説明します。  
  
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 表示される情報を決定する選択範囲の基礎について説明します、**プロパティ**ウィンドウ。  
  
 [プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)  
 目的について説明します、**プロパティ**ウィンドウ オブジェクトのリストを記述する方法については、この一覧から別のオブジェクトの呼び出しがトリガーされると、環境は通知新しいオブジェクトが選択されています。  
  
 [プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)  
 表示される 4 つの既定のボタンの目的について説明します、**プロパティ** ウィンドウのツールバー。  
  
 [プロパティ表示グリッド](../../extensibility/internals/properties-display-grid.md)  
 グリッドのプロパティの名前とプロパティの値のフィールドが検出された場所について説明します。  
  
 [プロパティ ウィンドウの選択の追跡の発表](../../misc/announcing-property-window-selection-tracking.md)  
 選択の追跡について説明します、**プロパティ**ウィンドウ。  
  
 [子プロパティを持つ非表示のプロパティ](../../misc/hiding-properties-that-have-child-properties.md)  
 実装することで、子プロパティを持つプロパティを非表示にする方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>インターフェイス。  
  
 [カスタム プロパティ ウィンドウの提供](../../misc/providing-a-custom-properties-window.md)  
 プロパティ ブラウザーを提供するための手順をについて説明します。  
  
 [[プロパティ] ウィンドウからのフィールドの説明の取得](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 選択したプロパティ フィールドに関連する情報を表示する説明の領域を検索する場所について説明します。  
  
 [[プロパティ] ウィンドウでプロパティ値を更新](../../misc/updating-property-values-in-the-properties-window.md)  
 保持する 2 つの方法を表示する手順について説明します、**プロパティ**ウィンドウは、プロパティ値の変更と同期します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 構成要素としてプロジェクトについて説明します、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。  
  
 [コードのコンパイルとビルド](../../ide/compiling-and-building-in-visual-studio.md)  
 使用する方法について説明します、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]継続的にテストし、アプリケーションを作成、アプリケーションをデバッグするためのプラットフォームです。  
  
 [HTML ドキュメントのプロパティと [プロパティ] ウィンドウ](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 [プロパティ] ウィンドウから直接 HTML ドキュメントを編集する方法について説明し、[プロパティ] ウィンドウで、HTML ドキュメント内のフィールドの一覧表を提供します。  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 について説明します、 `IDispatch` 、最初にアクセスして、メソッドとオブジェクトのプロパティに関する情報を取得する遅延バインディング メカニズムを提供するオートメーションをサポートするために設計されたインターフェイスです。  
  
 [NIB: 動的プロパティ (Visual Studio) の概要](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 アプリケーションのコンパイル済みコードではなく、外部構成ファイルでプロパティ値が格納されているように、アプリケーションを構成できる動的プロパティの概要を示します。  
  
 [NIB: プロジェクトのコンテナーとして](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 プロジェクトをソリューションに論理的に管理し、ビルド、および、デバッグ、アプリケーションを構成する項目のコンテナーとしての役割について説明します。  
  
 [NIB: プロジェクトのプロパティ](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 プロジェクトがプロジェクト全体に適用されるコントロールのプロパティとも、プロジェクトの特定のビルド構成に限定されているプロパティを使用する設定を管理する方法について説明します。  
  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]参照、データ接続、フォルダー、およびソリューションとプロジェクトを通じて、開発作業に必要なファイルなどの項目を効率的に管理します。  
  
 [Visual Studio の他の部分の拡張](../../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] サービスを使用して、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の他の部分に相当する UI 要素を作成する方法について説明します。

