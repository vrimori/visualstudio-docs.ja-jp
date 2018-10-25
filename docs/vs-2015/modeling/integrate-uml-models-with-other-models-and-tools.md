---
title: UML モデルを統合する他のモデルとツール |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a1107856f5889b9014605854bb036c56989c5930
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858057"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>UML モデルを他のモデルおよびツールと統合する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML モデルは、他のモデルやドメイン固有の言語に統合することができます。  
  
 さまざまな機能を実行する拡張機能のコードを記述して、次の方法でモデルを統合できます。  
  
 任意の要素からの参照を、ファイルなどの他の項目、または他のモデル内の要素にアタッチします。  
 UML 要素の場合、他の UML 要素、ファイル、またはその他のオブジェクトへのリンクを格納するために、それらの身元を文字列としてエンコードすることができます。  
  
 たとえば、UML アクション (つまり、アクティビティ図の要素) を別のアクティビティ図にリンクできる拡張機能を記述することができます。 ユーザーがアクションをダブルクリックすると、別のアクティビティ図が表示されます。 これでユーザーは、アクションに関する詳細なビューを提供できます。  
  
 文字列やその他のデータを要素に格納するには、次の 2 つの方法があります。  
  
- **ステレオタイプ プロパティ。** UML プロファイルを定義し、その中で定義するステレオタイプを使って、指定する種類の UML 要素にプロパティを追加できます。 たとえば、という名前のプロパティを追加するプロファイルを定義できます**MoreDetail** UML アクションにします。 ステレオタイプをアクションに適用してからリンク データをプロパティに格納することで、データをアクションに格納する拡張機能のコードを記述することができます。  
  
   ステレオタイプとそのプロパティは、[プロパティ] ウィンドウでユーザーが表示することができます。  
  
   この拡張機能を配置するには、プロファイル定義と拡張機能のコードを 1 つの [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能にパッケージ化します。  
  
   詳細については、次を参照してください。 [UML を拡張するプロファイルを定義して](../modeling/define-a-profile-to-extend-uml.md)します。  
  
   プロファイルがメニュー コマンドやジェスチャ ハンドラーと共にデプロイされているサンプル プロジェクトでは、次を参照してください。[サンプル: UML プロファイル](http://go.microsoft.com/fwlink/?LinkID=213811)します。  
  
- **参照。** 一連の文字列を任意の UML 要素にアタッチできます。 ファイル名や別の要素の GUID などの情報を格納するコードを記述することもできます。 これは、追加の定義を行わなくても行えます。 参照は、ユーザーには直接表示されません。  
  
   詳細については、次を参照してください。[モデル要素を UML に参照文字列をアタッチ](../modeling/attach-reference-strings-to-uml-model-elements.md)します。 サンプルについては、次を参照してください。[リンクの UML 要素を図または他のファイルに](http://go.microsoft.com/fwlink/?LinkId=213813)します。  
  
  参照をモデル要素にエンコードするには次の 2 つの方法があります。  
  
- **GUID とファイル名**のターゲットのモデル要素とそれを含むモデルまたはそれを表示する特定のダイアグラム。  
  
   例については、次を参照してください。[リンクの UML 要素を図または他のファイルに](http://go.microsoft.com/fwlink/?LinkId=213813)します。  
  
- **ModelBus 参照。** ModelBus は、モデル間の参照を作成および解決するためのフレームワークです。 これには、モデル内の要素をユーザーが選択できるようにする ModelBus ピッカーが含まれます。 これは、対象のモデルに変更があったために失われた参照をユーザーが解決するのにも役立ちます。  
  
   詳細については、次を参照してください。 [Visual Studio modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)します。  
  
  1 つのモデルから別のモデルに変更を反映します。  
  たとえば、1 つの要素の名前をリンクされた図の名前と同期させると、一方がユーザーによって変更されると他方も変更されるようになります。 これを行うための次の 2 つのメカニズムがあります。  
  
1. **VMSDK ルール**同じモデル内で変更を反映するために使用できます。  
  
    例については、次を参照してください。[リンクの UML 要素を図または他のファイルに](http://go.microsoft.com/fwlink/?LinkId=213813)します。  
  
2. **VMSDK イベント**など、モデルの外部の変更を反映する、リンクされたドキュメントのファイル名を変更する、または別のモデル内の要素を変更するために使用できます。  
  
   これら両方のメカニズムについては、次を参照してください。[方法: UML モデルの変更に応答](../misc/how-to-respond-to-changes-in-a-uml-model.md)します。  
  
   1 つのモデルから別のモデルに要素をドラッグしてコピーする  
   UML 図に項目をドラッグすることによって要素を作成できる機能をユーザーに提供することができます。 作成した要素は、オリジナルのコピーである必要はありません。 たとえば、ソリューション エクスプローラーからアクティビティ図を別のアクティビティ図にドラッグして新しいアクションを作成する機能をユーザーに提供することができます。  
  
   詳細については、次を参照してください。[モデリング図にジェスチャ ハンドラーを定義](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)と[方法: ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)します。  
  
## <a name="samples"></a>サンプル  
 コード サンプルを参照してください[リンクの UML 要素を図または他のファイルに](http://go.microsoft.com/fwlink/?LinkId=213813)します。 このサンプルを使用すると、ユーザーは任意の UML 要素にファイルをドラッグし、後でその要素をダブルクリックしてファイルを開くことができます。 たとえば、アクティビティ図を、ユースケース要素にリンクすることができます。 リンクが設定されている要素はアイコンで示されます。  
  
 このコード サンプルでは、以下の技法を説明します。  
  
- [UML モデル要素に参照文字列をアタッチする](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   このサンプル コードは、要素に関連付けられている参照文字列にファイル パスと要素 GUID を格納します。  
  
- UML 要素にデコレータを追加する方法。 デコレータの全般については、次を参照してください。[をカスタマイズするテキストおよびイメージ フィールド](../modeling/customizing-text-and-image-fields.md)します。  
  
   サンプルは、UML 図形にイメージのデコレータを追加します。  
  
- [方法: UML モデル内で変更に応答する](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   このサンプルでは、図に表示される新しい図形に応答するルールを定義する方法を示します。  
  
- [モデリング図にメニュー コマンドを定義する](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [モデリング図にジェスチャ ハンドラーを定義する](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   このサンプルでは、Windows エクスプローラー (またはエクスプローラー)、ソリューション エクスプローラー、およびその他の UML 要素からドラッグした項目を処理する方法について説明しています。  
  
  DSL で読み取る UML モデルの例を参照してください[方法: ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)します。  
  
## <a name="see-also"></a>関連項目  
 [モデリング図にメニュー コマンドを定義します。](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [モデリング図にジェスチャ ハンドラーを定義します。](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [方法: ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [方法: UML モデルの変更に対応](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [サンプル: UML プロファイル](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [UML 要素を図または他のファイルにリンク](http://go.microsoft.com/fwlink/?LinkId=213813)



