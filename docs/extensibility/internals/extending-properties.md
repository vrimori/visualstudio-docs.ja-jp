---
title: "プロパティの拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>プロパティを拡張します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **プロパティ**ウィンドウはすべてサポートしています、COM と COM + コンポーネントの汎用プロパティ ブラウザー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]製品です。 **プロパティ**ウィンドウは`ITypeInfo`情報および COM + 統合開発環境 (IDE) でその他のウィンドウで現在選択されているオブジェクトのデザイン時プロパティの一覧にメタデータを入力します。  
  
 **プロパティ** ウィンドウをキーボードで、f4 キーを押すかを選択すると開くことが**プロパティ ウィンドウ**上、**ビュー**を表示および選択したオブジェクトの構成に依存しない、デザイン時のプロパティおよびイベントの編集 メニューを使用します。 ソリューションやプロジェクトに関連付けられている構成に依存するプロパティに表示される[プロパティ ページ](../../extensibility/internals/property-pages.md)します。 詳細については、次を参照してください。 [NIB: プロジェクトのプロパティの](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)、[構成オプションを管理する](../../extensibility/internals/managing-configuration-options.md)、および[プロジェクトにおける NIB: 項目の管理](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)します。  
  
 ![プロパティ ウィンドウの概要](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
[プロパティ] ウィンドウ  
  
 このセクションの個々 の領域に関連する詳細な情報を提供する、**プロパティ**ウィンドウを実装する必要がありますインターフェイス ドメインおよびウィンドウの設定への呼び出しです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロパティ ウィンドウの概要](../../extensibility/internals/properties-window-overview.md)  
 説明、**プロパティ**ツール ウィンドウとドキュメント ウィンドウのウィンドウです。  
  
 [テンプレートのポリシーおよび [プロパティ] ウィンドウ](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 エンタープライズ テンプレート プロジェクトでは、プロジェクトが含まれている方法と、そのエンタープライズ テンプレート プロジェクトがポリシーを適用する方法について説明します。  
  
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 選択範囲内に表示される情報を決定するための基礎を説明、**プロパティ**ウィンドウです。  
  
 [プロパティ ウィンドウのオブジェクトの一覧](../../extensibility/internals/properties-window-object-list.md)  
 目的を記述、**プロパティ**ウィンドウ オブジェクトの一覧を記述する方法、この一覧から別のオブジェクトには、呼び出しがトリガーされた環境が通知され、新しいオブジェクトが選択されています。  
  
 [プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)  
 表示される&4; つの既定のボタンの説明、**プロパティ**ウィンドウのツールバー。  
  
 [プロパティ グリッドの表示](../../extensibility/internals/properties-display-grid.md)  
 グリッドでプロパティの名前とプロパティの値フィールドの検出が必要とされる場合について説明します。  
  
 [プロパティ ウィンドウの選択の追跡の発表](../../misc/announcing-property-window-selection-tracking.md)  
 選択範囲の追跡について説明します、**プロパティ**ウィンドウです。  
  
 [子プロパティを持つ非表示のプロパティ](../../misc/hiding-properties-that-have-child-properties.md)  
 実装することによって、子プロパティを持つプロパティを非表示にする方法について説明します<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>。  
  
 [カスタム プロパティ ウィンドウの提供](../../misc/providing-a-custom-properties-window.md)  
 プロパティ ブラウザーを提供するための手順を詳しく説明します。  
  
 [[プロパティ] ウィンドウからのフィールドの説明の取得](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 選択されているプロパティ フィールドに関連する情報が表示される説明領域の問い合わせ先について説明します。  
  
 [[プロパティ] ウィンドウでプロパティ値を更新](../../misc/updating-property-values-in-the-properties-window.md)  
 ステップ バイ ステップの説明を保持する&2; つの方法を示す、**プロパティ**ウィンドウは、プロパティ値の変更と同期します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 プロジェクトのビルド ブロックとしてについて説明して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 [コードのコンパイルとビルド](../../ide/compiling-and-building-in-visual-studio.md)  
 使用する方法について説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]連続的にテストおよびビルドしながら、アプリケーションをデバッグするためのプラットフォームです。  
  
 [HTML ドキュメントのプロパティと [プロパティ] ウィンドウ](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 [プロパティ] ウィンドウから直接 HTML ドキュメントを編集する方法について説明し、[プロパティ] ウィンドウで HTML ドキュメント内のフィールドの一覧表を提供します。  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 説明、`IDispatch`インターフェイスで、最初にアクセスし、メソッドとオブジェクトのプロパティに関する情報を取得するには、遅延バインディング メカニズムを提供するオートメーションをサポートするように設計されました。  
  
 [NIB: 動的なプロパティ (Visual Studio) の概要](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 プロパティの値は、アプリケーションのコンパイル済みコードではなく、外部構成ファイルに格納されるように、アプリケーションを構成できる動的なプロパティの概要を示します。  
  
 [NIB: コンテナーとしてのプロジェクト](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 プロジェクトの論理的な管理、ビルド、およびアプリケーションを構成する項目をデバッグするソリューション内のコンテナーとしての役割について説明します。  
  
 [NIB: プロジェクトのプロパティ](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 プロジェクトがプロジェクト全体に適用されるコントロールのプロパティとも、プロジェクトの特定のビルド構成に制限されているプロパティを使用する設定を管理する方法について説明します。  
  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]参照、データ接続、フォルダー、およびソリューションとプロジェクトを通じて、開発作業に必要なファイルなどの項目を効率的に管理します。  
  
 [Visual Studio の他の部分を拡張します。](../../extensibility/extending-other-parts-of-visual-studio.md)  
 使用する方法について説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の残りの部分に一致する UI 要素を作成するためサービス[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。
