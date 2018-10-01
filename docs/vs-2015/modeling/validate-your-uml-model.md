---
title: UML モデルの検証 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 42e0733668a1f96dc1881d4d4d58a575eeb9eb64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536803"
---
# <a name="validate-your-uml-model"></a>UML モデルの検証
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML モデルの検証](https://docs.microsoft.com/visualstudio/modeling/validate-your-uml-model)です。  
  
Visual Studio で描画できる UML モデルの一部が、プロジェクトでは無効と見なされる場合があります。 たとえば、ユース ケースのアクターを表す生存線のあるシーケンス図には必ずユース ケースをリンクするように求める場合があります。 インストールするか、定義*制約*このような要件に準拠するようにチームを支援します。 制約は、ユーザーがモデルを保存するときまたは開くときに適用することが可能で、メニュー コマンドで呼び出すことができます。  
  
 制約は、チームが UML モデルをどのように解釈して使用するかによって異なるため、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] には制約は付属していません。 しかし、独自の制約を定義したり、他のユーザーが定義した制約をインストールしたりすることはできます。 制約を定義し、配布用にパッケージ化する方法については、次を参照してください。 [UML モデルの検証制約を定義](../modeling/define-validation-constraints-for-uml-models.md)します。  
  
## <a name="invoking-validation"></a>検証の呼び出し  
 検証拡張機能のインストールが完了している場合、それによって提供される制約は、次のケースで適用できます。 一部の制約は、これらのケースの一部でのみ適用されるように設定されています。  
  
-   **検証コマンド。** いつでも検証を呼び出す次のようにクリックします。 **UML モデルの検証**上、**アーキテクチャ**メニュー。  
  
    > [!NOTE]
    >  検証制約がインストールされている場合に限り、コマンドが表示されます。  
  
-   **でモデルを保存しています。** モデルを保存するとき、検証制約を適用できます。 これらの制約の目的は、プロジェクトの解釈に従った場合に無効であるモデルが保存されることがないようにすることです。  
  
     エラーがある場合は、モデルを保存するかどうかを確認するメッセージが表示されます。 エラーを修正するか、またはモデルをそのまま保存するかを選択することができます。  
  
-   **モデルを開くとき。** モデルを開くときに、検証メソッドを適用して、モデルを保存したときに存在していたエラー メッセージを復元できます。 エラーは、1 つのモデルの異なる部分で作業していた複数のユーザーによって加えられた変更の間の不整合が原因で発生する場合もあります。 詳細については、次を参照してください。[モデルおよびエクスポート ダイアグラムの共有](../modeling/share-models-and-exporting-diagrams.md)します。  
  
 検証エラーは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] エラー ウィンドウで報告されます。  
  
 図の中でエラーが発生している要素を選択するには、エラーをダブルクリックします。 この操作は、エラーが発生している要素を、開いている図に表示できる場合に限り有効です。  
  
## <a name="installing-validation-constraints"></a>検証制約のインストール  
 制約は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張 (VSIX) ファイル内にパッケージ化されます。 通常、一連の制約は、メニュー コマンド、プロファイル、ツールボックス項目などの他の定義も含んだ拡張機能の一部となります。  
  
#### <a name="to-install-a-visual-studio-extension"></a>Visual Studio 拡張機能をインストールするには  
  
1.  ダブルクリックして、 **.vsix** Windows エクスプ ローラー (またはファイル エクスプ ローラー) でのファイル。  
  
2.  既に実行されている [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のインスタンスを再起動します。  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>検証制約の無効化およびインストール  
 制約を適用しないモデルを操作するとき、制約を含んだ拡張機能を一時的に無効にすることができます。 この方法により、各種の拡張機能を有効または無効にして、さまざまなモデルを個別に操作できます。  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Visual Studio 拡張機能を無効化またはアンインストールするには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **ツール** メニューのをクリックして**拡張機能と更新**します。  
  
2.  拡張機能、と共に次のようにクリックします。**を無効にする**、拡張機能を一時的に無効にします。 返すことによって後で有効再ことができます、**拡張機能と更新**ウィンドウ。  
  
     \- または -  
  
     クリックして**アンインストール**拡張機能を削除します。  
  
3.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] を再起動します。  
  
## <a name="see-also"></a>関連項目  
 [UML モデルの検証制約を定義します。](../modeling/define-validation-constraints-for-uml-models.md)   
 [アプリのモデルを作成します。](../modeling/create-models-for-your-app.md)   
 [開発プロセス内でのモデルの使用](../modeling/use-models-in-your-development-process.md)



