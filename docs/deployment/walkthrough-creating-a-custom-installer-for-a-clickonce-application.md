---
title: 'チュートリアル: ClickOnce アプリケーションのカスタム インストーラーを作成する |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e16ec76a6c820afc672bf38729c18b92cf2cdf8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025658"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>チュートリアル: ClickOnce アプリケーションのカスタム インストーラーを作成します。
ClickOnce アプリケーションがに基づいて、 *.exe*ファイルをサイレント モードでインストールされているし、カスタム インストーラーによって更新します。 カスタム インストーラーは、セキュリティとメンテナンス操作のためのカスタム ダイアログ ボックスを含め、インストール中に、カスタムのユーザー エクスペリエンスを実装できます。 インストール操作を実行するカスタム インストーラーを使用して、<xref:System.Deployment.Application.InPlaceHostingManager>クラス。 このチュートリアルでは、ClickOnce アプリケーションをサイレント インストールするカスタム インストーラーを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>カスタム ClickOnce アプリケーション インストーラーを作成するには  
  
1.  ClickOnce アプリケーションでは、System.Deployment および System.Windows.Forms への参照を追加します。  
  
2.  アプリケーションに新しいクラスを追加し、任意の名前を指定します。 このチュートリアルでは、名前 `MyInstaller` を使用します。  
  
3.  次の追加`Imports`または`using`ステートメントを新しいクラスの先頭にします。  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  次のメソッドをクラスに追加します。  
  
     これらのメソッドを呼び出す<xref:System.Deployment.Application.InPlaceHostingManager>配置マニフェストをダウンロードする方法はインストール、ダウンロードして、ClickOnce キャッシュにアプリケーションをインストールするアクセス許可をユーザーに確認、適切なアクセス許可をアサートします。 カスタム インストーラーは、ClickOnce アプリケーションが事前に信頼されている、または、信頼の決定を遅らせることができますを指定できます、<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>メソッドの呼び出し。 このコードは、あらかじめアプリケーションを信頼します。  
  
    > [!NOTE]
    >  事前に信頼する割り当てられたアクセス許可は、カスタム インストーラーのコードのアクセス許可を超えることはできません。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  コードからのインストールには、呼び出し、`InstallApplication`メソッド。 たとえば、クラスの名前を付けた`MyInstaller`、呼び出すことができます`InstallApplication`次のようにします。  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>次の手順  
 ClickOnce アプリケーションでは、更新プロセス中に表示するカスタム ユーザー インターフェイスを含む、カスタムの更新ロジックも追加できます。 詳細については、「<xref:System.Deployment.Application.UpdateCheckInfo>」を参照してください。 ClickOnce アプリケーションを非表示することも標準的なスタート メニュー エントリ、ショートカット、およびプログラム追加と削除のエントリを使用して、`<customUX>`要素。 詳細については、次を参照してください。 [ \<entryPoint > 要素](../deployment/entrypoint-element-clickonce-application.md)と<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > 要素](../deployment/entrypoint-element-clickonce-application.md)