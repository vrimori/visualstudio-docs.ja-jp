---
title: 'ワークフロー デザイナー - 方法: Windows Communication Foundation コントラクト操作 (レガシ) を実装します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b069d8ca8c1adb72e2869eb59644e8abeff14ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979023"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>方法: Windows Communication Foundation コントラクト操作を実装する (レガシ)

このトピックでは、.NET Framework version 3.5、または、WinFX を対象とする従来の Windows ワークフロー デザイナーを使用して Windows Communication Foundation (WCF) のコントラクト操作を実装する方法について説明します。

ドラッグした後、 **ReceiveActivity**ツールボックスからワークフロー デザイン サーフェイスにアクティビティを作成する新しい[!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]コントラクトまたは既存のコントラクトをインポートして操作を実装します。 選択したり、コントラクトとその操作を作成する、[選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)です。

## <a name="to-implement-a-wcf-contract-operation"></a>WCF コントラクト操作を実装するには

1.  ダブルクリックして、 **ReceiveActivity**デザイナーのアクティビティ の横にある省略記号 をクリックして、 **ServiceOperationInfo**プロパティに、**プロパティ**ウィンドウです。

2.  次のいずれかの操作を行います。

    -   をクリックして**契約の追加** ダイアログ ボックスの右上隅にします。 新しい [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] コントラクトおよび操作が作成されます。

         - または -

    -   をクリックして**インポート** ダイアログ ボックスの右上隅にします。 [を参照して .NET の種類 ダイアログ ボックス (レガシ) を選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)が開きます。 必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。 コントラクトを選択し、クリックして**OK**です。

     コントラクトを作成またはインポートしたら、そのコントラクトに新しい操作を追加できます。 追加する新しい操作契約を選択し、をクリックして**Add 操作** ダイアログ ボックスの右上隅にします。 操作の追加が終了したら、手順 3. に進みます。

3.  関連付ける操作を選択、 **ReceiveActivity**アクティビティ。 操作の定義は、操作の名前、パラメータ、プロパティ、アクセス許可の設定を変更することにより、操作できます。

     名前を変更するに新しい名前を入力してください、**操作名**テキスト ボックス。

     クリックして、**パラメーター**タブは、操作のパラメーターにアクセスします。 パラメータの名前、型、方向の変更のほか、操作のパラメータの追加または削除を行うことができます。

     クリックして、**プロパティ**操作の操作の保護レベルおよびサポートされているメッセージ交換機能にアクセスするには、タブ。

     クリックして、**権限**タブ操作の実装を許可するグループを指定します。

4.  をクリックして**OK**と**ReceiveActivity**アクティビティが実装している操作の操作名が表示されます。

5.  配置内でその操作の実装を使用するワークフロー アクティビティ、 **ReceiveActivity**アクティビティ。

## <a name="see-also"></a>関連項目

- [[操作の選択] ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)