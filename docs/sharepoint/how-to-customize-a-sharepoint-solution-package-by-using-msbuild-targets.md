---
title: '方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 814af35e452bce86dd2a6ba780b9fca5fe9bb4d4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873198"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズします。
  MSBuild ターゲットを使用すると、コマンド プロンプトで、Visual Studio で SharePoint パッケージ ファイルを作成する方法をカスタマイズできます (*.wsp*)。 たとえば、中間ディレクトリからパッケージ化と、列挙するファイルを指定する MSBuild 項目グループを変更する MSBuild プロパティをカスタマイズできます。  
  
## <a name="customize-and-run-msbuild-targets"></a>カスタマイズ、および MSBuild のターゲットの実行  
 BeforeLayout および AfterLayout のターゲットをカスタマイズする場合は、追加、削除、またはパッケージがファイルの変更など、パッケージのレイアウトの前にタスクを実行できます。  
  
#### <a name="to-customize-the-beforelayout-target"></a>BeforeLayout ターゲットをカスタマイズするには  
  
1. メモ帳などのエディターを開き、次のコードを追加します。  
  
   ```xml  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
     <Target Name="BeforeLayout">  
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
     </Target>  
   </Project>  
   ```  
  
    この例では、このターゲットのパッケージ化する前にメッセージが表示されます。  
  
2. ファイルに名前を**CustomLayout.SharePoint.targets**、SharePoint プロジェクトのフォルダーに保存します。  
  
3. プロジェクトを開きます、そのショートカット メニューを開きを選択し、**プロジェクトのアンロード**します。  
  
4. **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開き、選択し、**編集**  *\<ProjectName > .vbproj*または**の編集** *\<ProjectName > .csproj*します。  
  
5. 後に、`Import`プロジェクト ファイルの末尾付近の行に、次の行を追加します。  
  
   ```xml  
   <Import Project="CustomLayout.SharePoint.targets" />  
   ```  
  
6. プロジェクト ファイルを保存して閉じます。  
  
7. **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開き、選択し、**プロジェクトの再読み込み**します。  
  
   プロジェクトを発行するときに、パッケージ化を開始する前に、メッセージが出力に表示されます。  
  
#### <a name="to-customize-the-afterlayout-target"></a>AfterLayout ターゲットをカスタマイズするには  
  
1. メニュー バーで、**ファイル** > **オープン** > **ファイル**します。  
  
2. **ファイルを開く**ダイアログ ボックスで、プロジェクト フォルダーに移動し、CustomLayout.target ファイルを選択および選択し、**オープン**ボタンをクリックします。  
  
3. 直前に、`</Project>`タグは、次のコードを追加します。  
  
   ```xml  
   <Target Name="AfterLayout">  
     <Message Importance="high" Text="In the AfterLayout Target"></Message>  
   </Target>  
   ```  
  
    この例では、このターゲットがパッケージ化された後、メッセージが表示されます。  
  
4. 保存して、ターゲット ファイルを閉じます。  
  
5. Visual Studio を再起動して、プロジェクトを開きます。  
  
   プロジェクトを発行するときに、パッケージの開始前に BeforeLayout メッセージが表示され、パッケージ化が完了したら、AfterLayout メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
