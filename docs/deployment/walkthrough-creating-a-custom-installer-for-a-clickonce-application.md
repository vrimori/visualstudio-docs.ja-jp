---
title: 'チュートリアル: ClickOnce アプリケーションのカスタム インストーラーの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdef0199aa55d6981761a20804f9f209a1a0fdc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565420"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>チュートリアル: ClickOnce アプリケーションのカスタム インストーラーの作成
.Exe ファイルに基づく ClickOnce アプリケーションをサイレントでインストールおよびカスタム インストーラーによって更新できます。 カスタム インストーラーは、インストール中に、セキュリティやメンテナンスの操作のカスタム ダイアログ ボックスを含むカスタム ユーザー エクスペリエンスを実装できます。 インストールの操作を実行するカスタム インストーラーを使用して、<xref:System.Deployment.Application.InPlaceHostingManager>クラスです。 このチュートリアルでは、ClickOnce アプリケーションをサイレント モードでインストール済みのカスタム インストーラーを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>カスタムの ClickOnce アプリケーションのインストーラーを作成するには  
  
1.  ClickOnce アプリケーションでは、System.Deployment および System.Windows.Forms への参照を追加します。  
  
2.  アプリケーションに新しいクラスを追加し、任意の名前を指定します。 このチュートリアルは、名前を使用して`MyInstaller`です。  
  
3.  次の追加`Imports`または`using`ステートメントを新しいクラスの先頭にします。  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  クラスに次のメソッドを追加します。  
  
     これらのメソッドを呼び出す<xref:System.Deployment.Application.InPlaceHostingManager>配置マニフェストをダウンロードする方法はインストール、ダウンロードして、ClickOnce キャッシュにアプリケーションをインストールするアクセス許可をユーザーに確認、適切なアクセス許可をアサートします。 カスタム インストーラーは、ClickOnce アプリケーションが事前に信頼されている、または、信頼の決定を任せることができますを指定できます、<xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>メソッドの呼び出しです。 このコードは、あらかじめアプリケーションを信頼します。  
  
    > [!NOTE]
    >  事前に信頼する割り当てられた権限は、コードのアクセス許可、カスタム インストーラーを超えることはできません。  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  コードからのインストールには、呼び出し、`InstallApplication`メソッドです。 たとえば、クラスの名前を付けた`MyInstaller`、呼び出すことができます`InstallApplication`次のようにします。  
  
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
 ClickOnce アプリケーションには、更新プロセス中に表示するカスタム ユーザー インターフェイスを含む、カスタムの更新ロジックを追加できます。 詳細については、「<xref:System.Deployment.Application.UpdateCheckInfo>」を参照してください。 ClickOnce アプリケーションできますも抑制される標準的なスタート メニュー エントリ、ショートカット、およびプログラム追加と削除のエントリを使用して、`<customUX>`要素。 詳細については、次を参照してください。 [ \<entryPoint > 要素](../deployment/entrypoint-element-clickonce-application.md)と<xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > 要素](../deployment/entrypoint-element-clickonce-application.md)