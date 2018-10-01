---
title: '方法: Windows Communication Foundation コントラクト操作 (レガシ) の実装 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f4277de8f97951847bf448636fec1b9c652f9359
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538826"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>方法: Windows Communication Foundation コントラクト操作を実装する (レガシ)
このトピックでは、[!INCLUDE[indigo1](../includes/indigo1-md.md)] または [!INCLUDE[wfd1](../includes/wfd1-md.md)] を対象とする従来の [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]を使用して [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] コントラクト操作を実装する方法について説明します。  
  
 ドラッグした後、 **ReceiveActivity**ワークフロー デザイン サーフェイスにアクティビティをツールボックスから、作成するか、新しい[!INCLUDE[indigo2](../includes/indigo2-md.md)]コントラクトまたは既存のコントラクトをインポートして、操作を実装します。 選択または作成のコントラクトとその操作を通じて、[選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)します。  
  
### <a name="to-implement-a-wcf-contract-operation"></a>WCF コントラクト操作を実装するには  
  
1.  ダブルクリック、 **ReceiveActivity**アクティビティ デザイナーの横にある省略記号をクリックしてまたは、 **ServiceOperationInfo**プロパティ、**プロパティ**ウィンドウ。  
  
2.  次のいずれかの操作を行います。  
  
    -   クリックして**契約の追加** ダイアログ ボックスの右上隅にします。 新しい [!INCLUDE[indigo2](../includes/indigo2-md.md)] コントラクトおよび操作が作成されます。  
  
         - または -  
  
    -   クリックして**インポート** ダイアログ ボックスの右上隅にします。 [参照し、.NET の種類 ダイアログ ボックス (レガシ) を選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)が開きます。 必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。 コントラクトを選択し、をクリックして**OK**します。  
  
     コントラクトを作成またはインポートしたら、そのコントラクトに新しい操作を追加できます。 新しい操作を追加する契約を選択し をクリックして**追加操作** ダイアログ ボックスの右上隅にします。 操作の追加が終了したら、手順 3. に進みます。  
  
3.  関連付ける操作を選択、 **ReceiveActivity**アクティビティ。 操作の定義は、操作の名前、パラメータ、プロパティ、アクセス許可の設定を変更することにより、操作できます。  
  
     名前を変更するには、新しい名前を入力、**操作名**テキスト ボックス。  
  
     をクリックして、**パラメーター**操作のパラメーターにアクセスするには、タブ。 パラメータの名前、型、方向の変更のほか、操作のパラメータの追加または削除を行うことができます。  
  
     をクリックして、**プロパティ**操作の操作の保護レベルでサポートされているメッセージの exchange 機能にアクセスするには、タブ。  
  
     をクリックして、**権限**タブは、操作を実装するために許可するグループを指定します。  
  
4.  をクリックして**OK**と**ReceiveActivity**アクティビティ実装しています。 操作の操作名が表示されます。  
  
5.  配置内でその操作の実装で使用するワークフロー アクティビティ、 **ReceiveActivity**アクティビティ。  
  
## <a name="see-also"></a>関連項目  
 [選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)