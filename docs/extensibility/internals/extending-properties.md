---
title: プロパティの拡張 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 095c9a81b6bd7d1c4eb75fafce6f3311b413581f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935541"
---
# <a name="extend-properties"></a>拡張プロパティ
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **プロパティ**ウィンドウはすべてサポートしています、COM と COM + コンポーネントのユニバーサル プロパティ ブラウザーを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]製品です。 **プロパティ**ウィンドウは`ITypeInfo`情報および COM + 統合開発環境 (IDE) でその他のウィンドウで現在選択されているオブジェクトのデザイン時プロパティの一覧にメタデータを入力します。  
  
 **プロパティ**ウィンドウで、キーを押して開くことができます**F4** 、キーボードの選択または**プロパティ ウィンドウ**上、**ビュー**  メニューの 構成に依存しない、デザイン時のプロパティとイベントを選択したオブジェクトの表示および編集に使用されます。 ソリューションやプロジェクトの関連付けの構成に依存するプロパティに表示される[プロパティ ページ](../../extensibility/internals/property-pages.md)します。 詳細については、[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)します。  
  
 ![プロパティ ウィンドウの概要](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
[プロパティ] ウィンドウ  
  
 このセクションの個々 の領域に関連する詳細な情報を提供する、**プロパティ**ウィンドウと、ウィンドウの設定への呼び出し、インターフェイスを実装する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロパティ ウィンドウの概要](../../extensibility/internals/properties-window-overview.md)  
 目的について説明します、**プロパティ**ツール ウィンドウとドキュメント ウィンドウのウィンドウ。  
  
 [テンプレートのポリシーと、[プロパティ] ウィンドウ](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 エンタープライズ テンプレート プロジェクトで、プロジェクトが含まれている方法と、そのエンタープライズ テンプレート プロジェクトがポリシーを適用する方法について説明します。  
  
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 表示される情報を決定する選択範囲の基礎について説明します、**プロパティ**ウィンドウ。  
  
 [プロパティ ウィンドウのオブジェクトの一覧](../../extensibility/internals/properties-window-object-list.md)  
 目的について説明します、**プロパティ**ウィンドウ オブジェクトのリストを記述する方法については、この一覧から別のオブジェクトの呼び出しがトリガーされると、環境は通知新しいオブジェクトが選択されています。  
  
 [プロパティ ウィンドウのボタン](../../extensibility/internals/properties-window-buttons.md)  
 表示される 4 つの既定のボタンの目的について説明します、**プロパティ** ウィンドウのツールバー。  
  
 [プロパティ グリッドの表示](../../extensibility/internals/properties-display-grid.md)  
 グリッドのプロパティの名前とプロパティの値のフィールドが検出された場所について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 構成要素としてプロジェクトについて説明します、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 [コンパイルとビルド](../../ide/compiling-and-building-in-visual-studio.md)  
 使用する方法について説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]継続的にテストし、アプリケーションを作成、アプリケーションをデバッグするためのプラットフォームです。  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 について説明します、 `IDispatch` 、最初にアクセスして、メソッドとオブジェクトのプロパティに関する情報を取得する遅延バインディング メカニズムを提供するオートメーションをサポートするために設計されたインターフェイスです。  
  
 [アプリケーション設定の管理 (.NET)](../../ide/managing-application-settings-dotnet.md)  
 アプリケーションのコンパイル済みコードではなく、外部構成ファイルでプロパティ値が格納されているように、アプリケーションを構成できるアプリケーションの設定の概要を示します。  
  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)  
 説明方法[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]参照、データ接続、フォルダー、およびソリューションとプロジェクトを通じて、開発作業に必要なファイルなどの項目を効率的に管理します。  
  
 [Visual Studio の他の部分を拡張します。](../../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] サービスを使用して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の他の部分に相当する UI 要素を作成する方法について説明します。