---
title: データ ユーザー インターフェイス要素 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.tablemappings
- vs.datasource.choosebindingsourcedialog
- vs.datasource.choosedatasourceinstancedlg
- vs.data.editrelation
- DSD_EditMultiKey
- vs.datasource.RealtionBuilder
- vs.xmldesigner.editkey
- vs.xmldesigner.choosekey
- vs.data.generatedataset
- vs.data.configurationerror
- vs.data.DSD_MissingConnections_Message
- vs.datasource.choosedesigndatasourcedlg
- vs.data.datapreview
- vs.data.editforeignkeyconstraint
- vs.datasource.choosedataconectordialog
- vs.data.dataadapterpreview
- vs.data.configurationwizard
- vs.data.datapreviewdialog
- DSD_EditMultiKeyHelpID
- vs.data.advancedoptions
- vs.data.previewscript
- vs.data.datasourcelogin
- vs.syncdesigner.syncnowconflictiondialog
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- dialog boxes, data
- data [Visual Studio], dialog boxes
ms.assetid: 90943baf-5bd1-4eef-927f-f82485979fde
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b699d44b8aa5b8c9e1e917e4e361414ff1a9afd4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533369"
---
# <a name="data-user-interface-elements"></a>データ ユーザー インターフェイス要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このセクションでは、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] または Visual C# アプリケーションでのデータ アクセスをデザインするときに使用するすべてのダイアログ ボックスとウィザードについて説明します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ スマート タグ](http://msdn.microsoft.com/en-us/1e0a848f-c57b-47ab-b884-eaaa40726f43)  
 データに対して使用できるスマート タグ コマンドについて説明します。  
  
 [データセットのダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/0e03c0ff-212b-4bfa-ac51-3c2adb71ead0)  
 既存のデータセットまたは新しい型指定されていないデータセットを入力 (のインスタンス、 **System.Data.Dataset**クラス) フォームまたはコンポーネントにします。  
  
 [SQL 高度なオプション ダイアログ ボックスの生成](http://msdn.microsoft.com/en-us/41420450-1ff4-4a1a-b85b-6f6901538fef)  
 更新、オプティミスティック コンカレンシーに対するオプションを指定し、データセットを更新することによって、データ アダプターに対する SQL ステートメントおよびストアド プロシージャの作成方法を制御できます。  
  
 [データ ソースのインスタンス ダイアログ ボックスを選択します。](http://msdn.microsoft.com/en-us/51c47f06-fdc5-453e-9178-0a5a2c5c9f34)  
 プロジェクトのデータセットの一覧から目的のデータセットを選択できます。  
  
 [ダイアログ ボックスとマージするデータ ソースを選択します。](http://msdn.microsoft.com/en-us/accafff7-f6bd-481c-a121-fe8a76cd681d)  
 複数のデータ ソースを使用できる場合に、マージするデータ ソースを選択できます。  
  
 [キーのダイアログ ボックスを選択します。](http://msdn.microsoft.com/en-us/4ddbfbb7-a80a-412a-b80d-291d86376ca3)  
 列が複数キー制約に関与する場合に、キーを選択できます。  
  
 [コレクション エディター](http://msdn.microsoft.com/library/030095bd-fb9a-4b21-b628-fc1cc5985bb7)  
 コレクションの各メンバーを作成および編集できるさまざまなコレクション エディターに関するトピックへのリンクを提供します。  
  
 [接続が見つかりません。](http://msdn.microsoft.com/en-us/bb9b2e12-7f76-4ee5-acbb-5d20116ee044)  
 アプリケーション設定に存在しない接続文字列への参照がデータセットに含まれている場合に通知します。  
  
 [データ アダプター構成エラー ダイアログ ボックス](http://msdn.microsoft.com/en-us/9ce65cd2-0c7d-4f51-8685-d68be5f3009b)  
 Visual Studio がデータ アダプターのインスタンスの作成とプロパティの設定を試行している間に発生した 1 つ以上のエラーを表示します。  
  
 [データ アダプタ構成ウィザード](http://msdn.microsoft.com/en-us/efff90cb-0e4c-4eb3-87dc-65dd9d418809)  
 データ アダプターがデータベースからデータセットにデータを読み込んだり、再び書き戻したりするために使用する SQL コマンドやストアド プロシージャを設定します。 このトピックでは、ウィザードの実行方法およびウィザードが完了した後の操作について説明します。  
  
 [データ アダプター プレビュー ダイアログ ボックス](http://msdn.microsoft.com/en-us/1f614cd3-4530-457e-84af-00ccbaea08cc)  
 データ アダプターによってデータセットにデータが入力される方法を確認できます。これは、アダプターが目的のデータを返すこと、テーブル マッピングが正しく動作すること、およびさまざまなパラメーター値の効果をテストする場合に役立ちます。  
  
 [データ ソースのログイン ダイアログ ボックス](http://msdn.microsoft.com/en-us/6f2d9a57-53c3-4841-bd37-a3643eb68d2e)  
 まだ認証されていないデータ ソース (通常はデータベース) へのアクセスを要求できます。  
  
 [[データセット] タブ、ツールボックス](http://msdn.microsoft.com/en-us/fa5f2d6f-924d-4262-ba1b-e9e7f90e7764)  
 型指定されたデータセットに追加できるオブジェクトを表示します。  
  
 [接続文字列 ダイアログ ボックスにパスワードを含めますか](http://msdn.microsoft.com/en-us/193696a7-5213-4396-8328-05ac2df6ee94)  
 接続文字列にパスワードを埋め込むかどうかを制御できます。  
  
 [キーのダイアログ ボックスを編集します。](http://msdn.microsoft.com/en-us/f5c80e39-3a42-4284-b222-6ca009fd9675)  
 キーを定義および編集できます。  
  
 [外部キー制約 ダイアログ ボックス](http://msdn.microsoft.com/en-us/45d15629-1f4d-40a7-8708-c9ddfebedc1e)  
 別のテーブルに関連付けられたデータセット テーブルの 1 つ以上の列に外部キー制約を設定できます。  
  
 [生成データセット ダイアログ ボックス](http://msdn.microsoft.com/en-us/c0efdbaf-13b1-4ee8-ade6-f8a784126cdc)  
 1 つ以上のデータ アダプターによって提供された情報から新しい型指定されたデータセットを生成したり、既存のデータセットにテーブルを追加したりできます。  
  
 [複数の BindingSources ダイアログ ボックス](http://msdn.microsoft.com/en-us/db76f70c-4fb5-479d-9b64-a67158d48f97)  
 複数の <xref:System.Windows.Forms.BindingSource> が使用可能な場合に、使用する <xref:System.Windows.Forms.BindingSource> を選択できます。  
  
 [データのプレビュー ダイアログ ボックス](http://msdn.microsoft.com/en-us/aa4f0d04-2695-4bb8-946d-54a97ae7287f)  
 プロジェクトのクエリによって返されたデータをレビューできます。  
  
 [プレビューの SQL スクリプト ダイアログ ボックス](http://msdn.microsoft.com/en-us/e9571e8b-821c-492d-9bc8-b44eba898bdd)  
 一部として表示されます、[データ アダプタ構成ウィザード](http://msdn.microsoft.com/en-us/efff90cb-0e4c-4eb3-87dc-65dd9d418809)ウィザードがデータを読み書きするストアド プロシージャの作成に使用する SQL スクリプトを確認するようにします。  
  
 [[リレーションシップ] ダイアログ ボックス](http://msdn.microsoft.com/en-us/ab8f4b0e-af4c-4725-a550-e2b2ebe43a02)  
 リレーションシップを作成することができます (、 **DataRelation**オブジェクト) データセット内の 2 つのデータ テーブル内の親と子レコードに関する情報を保持します。  
  
 [検索条件ビルダー ダイアログ ボックス](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)  
 データ バインド Windows フォームにパラメーター クエリを作成し、クエリの実行に必要なコントロールを自動的に追加できます。  
  
 [テーブル マッピング ダイアログ ボックス](http://msdn.microsoft.com/en-us/fb4cec1e-f3c8-4773-b409-c2de15293fea)  
 データベース テーブルまたは他のデータ ソースのどの列がデータセット テーブルの列に対応するかを指定できます。  
  
 [一意の制約 ダイアログ ボックス](http://msdn.microsoft.com/en-us/e71a60d7-fae2-4bd0-a1e8-43aae351707d)  
 型指定されていないデータセットのテーブルの 1 つ以上の列に UNIQUE 制約を設定できます。  
  
## <a name="related-sections"></a>関連項目  
 [データへのアクセス](../data-tools/accessing-data-in-visual-studio.md)  
 Visual Basic および Visual C# アプリケーションでデータにアクセスする方法を説明するトピックへのリンクを提供します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)