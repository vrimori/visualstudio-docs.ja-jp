---
title: 'チュートリアル: カスタム XAML をスタート ページに追加する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58c7441a4f910a1da35bc464e12ddba3bd5583bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802526"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>チュートリアル: カスタム XAML をスタート ページに追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、カスタム Visual Studio スタート ページを含む Web ブラウザーを作成する方法を示します。  
  
## <a name="adding-custom-xaml"></a>カスタム XAML を追加します。  
  
1.  次の手順で、[スタート] ページを作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)します。  
  
2.  MainWindow.xaml ファイルでは、検索、\<グリッド > セクション。  
  
3.  追加、 \<TabControl > 要素と\<TabItem > 内で、\<グリッド > 要素は、次の例に示すようにします。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  1 秒あたりの追加\<TabItem > で、\<ボタン > 要素を新しいプロジェクトを開きます。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>カスタム スタート ページのテスト  
  
1.  F5 キーを押します。  
  
     Visual Studio の実験用インスタンスのインストールが選択されていないカスタム スタート ページが表示されます。  
  
2.  Visual Studio の実験用インスタンスを開き、**ツール/Options/環境**ページ。  
  
3.  選択**スタートアップ**します。 **スタート ページのカスタマイズ**一覧で、.xaml ファイルを選択してクリックして**OK**。  
  
4.  **[表示]** メニューの **[スタート ページ]** をクリックします。  
  
5.  をクリックして、 **Bing**タブ。  
  
     Bing web ページが表示されます。  
  
6.  をクリックして、 **MyButton**タブ。  
  
     表示する必要があります、 **MyProject**ボタンを開きます、**新しいプロジェクト**ダイアログ。  
  
7.  実験用インスタンスを閉じます。  
  
## <a name="applying-the-custom-start-page"></a>カスタム スタート ページを適用します。  
  
#### <a name="to-test-the-custom-start-page"></a>カスタム スタート ページをテストするには  
  
1.  **ツール/オプション/環境**、**スタートアップ**します。 **スタート ページのカスタマイズ**一覧で、.xaml ファイルを選択してクリックして**OK**。  
  
## <a name="next-steps"></a>次の手順  
 これで、Visual Studio スタート ページには、Web ブラウザーのタブと [MyButton] タブを表示するタブが含まれています。使用してその他の機能を持つカスタム スタート ページを作成することができます、*コード ビハインド*ように、カスタムの .dll を追加するモデル[スタート ページにユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)します。 他のユーザーとカスタム スタート ページを共有するには、結果として得られる .vsix ファイルを発行することによって、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、または別の Web サイトやネットワーク共有です。 詳細については、「 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)   
 [コンテナーの WPF コントロール](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)

