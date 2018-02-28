---
title: "プロパティを拡張 |Microsoft ドキュメント"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 26cf161259736dbd2b2e26279842571d62f69352
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="extending-properties"></a>拡張プロパティ
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **プロパティ**ウィンドウはすべてサポートしています、COM と COM + コンポーネントのユニバーサル プロパティ ブラウザー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]製品です。 **プロパティ**ウィンドウは`ITypeInfo`情報および COM + 統合開発環境 (IDE) でその他のウィンドウで現在選択されているオブジェクトのデザイン時プロパティの一覧にメタデータを入力します。  
  
 **プロパティ**ウィンドウで開くことができます、キーボードの F4 キーを押すかを選択して**プロパティ ウィンドウ**上、**ビュー**を表示および編集 メニューを使用構成に依存しない、デザイン時のプロパティおよび選択したオブジェクトのイベントです。 ソリューションやプロジェクトに関連付けられている構成に依存するプロパティに表示される[プロパティ ページ](../../extensibility/internals/property-pages.md)です。 詳細については、[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)です。  
  
 ![プロパティ ウィンドウの概要](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
[プロパティ] ウィンドウ  
  
 このセクションの個々 の領域に関連する詳細な情報を提供する、**プロパティ**ウィンドウとインターフェイスを実装する必要がありますを呼び出すと、ウィンドウを設定します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロパティ ウィンドウの概要](../../extensibility/internals/properties-window-overview.md)  
 目的について説明、**プロパティ**ウィンドウのツール ウィンドウおよびドキュメント ウィンドウと比較しています。  
  
 [テンプレート ポリシーとプロパティ ウィンドウ](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 エンタープライズ テンプレート プロジェクトでは、プロジェクトが含まれている方法と、そのエンタープライズ テンプレート プロジェクトがポリシーを適用する方法について説明します。  
  
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 表示される情報を決定する選択範囲の基礎について説明します、**プロパティ**ウィンドウです。  
  
 [プロパティ ウィンドウのオブジェクト一覧](../../extensibility/internals/properties-window-object-list.md)  
 目的を記述、**プロパティ**ウィンドウ オブジェクトの一覧を記述する方法については、この一覧から別のオブジェクトには、呼び出しがトリガーされたときに、環境十分な情報に基づいて、新しいオブジェクトが選択されています。  
  
 [プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)  
 表示される 4 つの既定のボタンの説明、**プロパティ**ウィンドウのツールバー。  
  
 [プロパティ表示グリッド](../../extensibility/internals/properties-display-grid.md)  
 ここで、プロパティ名とプロパティ値フィールドは、「グリッドについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 プロジェクトのビルド ブロックとしてについて説明して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 [コードのコンパイルとビルド](../../ide/compiling-and-building-in-visual-studio.md)  
 使用する方法について説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プラットフォームを継続的にテストし、それらを作成すると、アプリケーションをデバッグします。  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 について説明します、`IDispatch`インターフェイスで、最初にアクセスして、メソッドとオブジェクトのプロパティに関する情報を取得する遅延バインディング メカニズムを提供するオートメーションをサポートするように設計されました。  
  
 [アプリケーションの設定 (.NET) の管理](../../ide/managing-application-settings-dotnet.md)  
 プロパティの値は、アプリケーションのコンパイル済みコードの代わりに、外部構成ファイルに格納されるように、アプリケーションを構成できるアプリケーションの設定の概要を示します。  
  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]参照、データ接続、フォルダー、およびソリューションとプロジェクトを開発作業に必要なファイルなどのアイテムを効率よく管理します。  
  
 [Visual Studio の他の部分の拡張](../../extensibility/extending-other-parts-of-visual-studio.md)  
 使用する方法について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の残りの部分に一致する UI 要素を作成するサービス[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。