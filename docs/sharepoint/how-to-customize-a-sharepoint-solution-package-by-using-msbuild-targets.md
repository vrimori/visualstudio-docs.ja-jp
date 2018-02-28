---
title: "方法: MSBuild のターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ab9aa26efe3002c28ec031457d2732c828eca445
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする
  MSBuild のターゲットを使用すると、コマンド プロンプトで、Visual Studio で SharePoint パッケージ ファイル (.wsp) を作成する方法をカスタマイズすることができます。 たとえば、パッケージの中間ディレクトリと MSBuild 項目グループを列挙するファイルを指定を変更する MSBuild プロパティをカスタマイズできます。  
  
## <a name="customizing-and-running-msbuild-targets"></a>カスタマイズして、MSBuild のターゲットを実行しています。  
 BeforeLayout および AfterLayout のターゲットをカスタマイズする場合は、追加、削除、またはパッケージがファイルの変更など、パッケージ レイアウトの前にタスクを実行できます。  
  
#### <a name="to-customize-the-beforelayout-target"></a>BeforeLayout ターゲットをカスタマイズするには  
  
1.  メモ帳などのエディターを開き、次のコードを追加します。  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     この例では、この対象のパッケージ化する前にメッセージを表示します。  
  
2.  ファイルの名前を付けます**CustomLayout.SharePoint.targets**、SharePoint プロジェクトのフォルダーに保存します。  
  
3.  プロジェクトを開き、そのショートカット メニューを開きを選択し**プロジェクトのアンロード**です。  
  
4.  **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開きを選択し、**編集***ProjectName***.vbproj**または**編集***ProjectName***.csproj**です。  
  
5.  後に、`Import`プロジェクト ファイルの末尾付近の行、次の行を追加します。  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  プロジェクト ファイルを保存して閉じます。  
  
7.  **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開きを選択し、**プロジェクトの再読み込み**です。  
  
 プロジェクトを発行するときに、パッケージが開始する前に、メッセージが出力に表示されます。  
  
#### <a name="to-customize-the-afterlayout-target"></a>AfterLayout ターゲットをカスタマイズするには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**開く**、**ファイル**です。  
  
2.  **ファイルを開く**ダイアログ ボックスで、プロジェクト フォルダーに移動 CustomLayout.target ファイルを選択しを選択し、**開く**ボタンをクリックします。  
  
3.  直前に、`</Project>`タグは、次のコードを追加します。  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     この例では、このターゲットがパッケージ化された後、メッセージが表示されます。  
  
4.  保存して、ターゲット ファイルを閉じます。  
  
5.  Visual Studio を再起動し、プロジェクトを開きます。  
  
 プロジェクトを発行するときに、BeforeLayout メッセージをパッケージ化が開始する前に表示され、パッケージ化が完了したら、AfterLayout メッセージが表示されます。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  