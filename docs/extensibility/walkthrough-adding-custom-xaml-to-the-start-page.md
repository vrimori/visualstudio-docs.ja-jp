---
title: "チュートリアル: カスタム XAML をスタート ページに追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 924a6e2640002bc47eb75c903c46b5a170a9c308
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>チュートリアル: カスタム XAML をスタート ページに追加します。
このチュートリアルでは、カスタム Visual Studio スタート ページを含む Web ブラウザーを作成する方法を示します。  
  
## <a name="adding-custom-xaml"></a>カスタム XAML を追加します。  
  
1.  次の手順で、スタート ページを作成する[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)です。  
  
2.  MainWindow.xaml ファイルの検索、\<グリッド > セクションでします。  
  
3.  追加、 \<TabControl > 要素と\<TabItem > 内、\<グリッド > 要素を次の例で示すようにします。  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  1 秒あたりの追加\<TabItem > で、\<ボタン > プロジェクトを開き、新しい要素。  
  
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
  
2.  Visual Studio の実験用インスタンスの開く、**ツール//環境**ページ。  
  
3.  選択**スタートアップ**です。 **スタート ページのカスタマイズ**一覧で、.xaml ファイルを選択し、をクリックして**OK**です。  
  
4.  **[表示]** メニューの **[スタート ページ]**をクリックします。  
  
5.  クリックして、 **Bing**タブです。  
  
     Bing web ページが表示されます。  
  
6.  クリックして、 **MyButton**タブです。  
  
     参照する必要があります、 **MyProject**  ボタンを開きます、**新しいプロジェクト**ダイアログ。  
  
7.  実験用インスタンスを閉じます。  
  
## <a name="applying-the-custom-start-page"></a>カスタム スタート ページを適用します。  
  
#### <a name="to-test-the-custom-start-page"></a>カスタム スタート ページをテストするには  
  
1.  **ツール/オプション/環境****スタートアップ**です。 **スタート ページのカスタマイズ**一覧で、.xaml ファイルを選択し、をクリックして**OK**です。  
  
## <a name="next-steps"></a>次の手順  
 これで、Visual Studio のスタート ページには、Web ブラウザーのタブと [MyButton] タブを表示するタブが含まれています。使用して、その他の機能を持つカスタムのスタート ページを作成することができます、*コード ビハインド*に示すように、カスタムの .dll を追加するモデル[スタート ページにユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)です。 他のユーザーとカスタム スタート ページを共有するには、結果として得られる .vsix ファイルを発行することによって、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、または別の Web サイトやネットワークを共有します。 詳細については、次を参照してください。[カスタム スタート ページの配置](../extensibility/deploying-custom-start-pages.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)   
 [コンテナーの WPF コントロール](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)