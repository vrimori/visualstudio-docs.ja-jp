---
title: 'チュートリアル: カスタム XAML をスタート ページに追加する |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a828fe6f7944e2bb0d9527d781c66630ed1f3879
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947284"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>チュートリアル: カスタム XAML をスタート ページに追加します。
このチュートリアルでは、カスタム Visual Studio スタート ページを含む Web ブラウザーを作成する方法を示します。  
  
## <a name="adding-custom-xaml"></a>カスタム XAML を追加します。  
  
1.  次の手順で、[スタート] ページを作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)します。  
  
2.  *MainWindow.xaml*ファイルで、検索、\<グリッド > セクション。  
  
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
  
1.  **F5**キーを押します。  
  
     Visual Studio の実験用インスタンスのインストールが選択されていないカスタム スタート ページが表示されます。  
  
2.  Visual Studio の実験用インスタンスを開き、**ツール/Options/環境**ページ。  
  
3.  選択**スタートアップ**します。 **スタート ページのカスタマイズ**一覧で、、 *.xaml*ファイルを開き、をクリックして**OK**します。  
  
4.  **[表示]** メニューの **[スタート ページ]** をクリックします。  
  
5.  をクリックして、 **Bing**タブ。  
  
     Bing web ページが表示されます。  
  
6.  をクリックして、 **MyButton**タブ。  
  
     表示する必要があります、 **MyProject**ボタンを開きます、**新しいプロジェクト**ダイアログ。  
  
7.  実験用インスタンスを閉じます。  
  
## <a name="apply-the-custom-start-page"></a>カスタム スタート ページを適用します。  
  
### <a name="to-test-the-custom-start-page"></a>カスタム スタート ページをテストするには  
  
1.  **ツール/オプション/環境**、**スタートアップ**します。 **スタート ページのカスタマイズ**一覧で、、 *.xaml*ファイルを開き、をクリックして**OK**します。  
  
## <a name="next-steps"></a>次の手順  
 これで、Visual Studio スタート ページには、Web ブラウザーのタブと [MyButton] タブを表示するタブが含まれています。使用してその他の機能を持つカスタム スタート ページを作成することができます、*コード ビハインド*ように、カスタムの .dll を追加するモデル[スタート ページにユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)します。 他のユーザーとカスタム スタート ページを共有するには、結果として得られる .vsix ファイルを発行することによって、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、または別の Web サイトやネットワーク共有です。 詳細については、「 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページをカスタマイズします。](../ide/customizing-the-start-page-for-visual-studio.md)   
 [コンテナーの WPF コントロール](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)