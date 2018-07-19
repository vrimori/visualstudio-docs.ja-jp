---
title: '方法: SignTool.exe (ClickOnce) を持つファイルを使用してセットアップ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081502"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>方法: SignTool.exe (ClickOnce) を持つファイルを使用してセットアップ
使用することができます*SignTool.exe*セットアップ プログラムに署名する (*setup.exe*)。 このプロセスによって、改ざんされたファイルがエンド ユーザーのコンピューターにインストールされないようにすることができます。  
  
 既定で、ClickOnce には複数の署名されたマニフェストと、1 つの署名されたセットアップ プログラムがあります。 ただし、後でセットアップ プログラムのパラメーターを変更する場合、セットアップ プログラムに後で署名する必要があります。 セットアップ プログラムの署名後にパラメーターを変更すると、署名が破損します。  
  
 次の手順では、未署名のマニフェストと未署名のセットアップ プログラムを生成します。 次に、ClickOnce の署名を Visual Studio で有効にし、署名されたマニフェストを生成します。 セットアップ プログラムは未署名のままなので、ユーザーは自分の証明書を使用して実行可能ファイルに署名できます。  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>未署名のセットアップ プログラムを生成し、後で署名するには  
  
1.  マニフェストに署名する証明書を開発用コンピューターにインストールします。  
  
2.  プロジェクトを選択**ソリューション エクスプ ローラー**します。  
  
3.  **プロジェクト** メニューのをクリックして*ProjectName* **プロパティ**します。  
  
4.  **署名** ページでクリア**ClickOnce マニフェストに署名**します。  
  
5.  **発行**] ページで [**の前提条件**します。  
  
6.  すべての前提条件が選択されていることを確認し、をクリックして**OK**します。  
  
7.  **発行**ページで発行設定を確認し、をクリックし、**今すぐ発行**します。  
  
     ソリューションは、未署名のアプリケーション マニフェスト、未署名の配置マニフェスト、バージョン固有のファイル、および未署名のセットアップ プログラムを発行フォルダーに発行します。  
  
8.  **発行**] ページで [**の前提条件**します。  
  
9. **の前提条件**、ダイアログ ボックスをオフ**必須コンポーネントをインストールするセットアップ プログラムを作成**です。  
  
10. **発行**ページで発行設定を確認し、をクリックし、**今すぐ発行**します。  
  
     ソリューションは、署名済みのアプリケーション マニフェスト、署名済みの配置マニフェスト、およびバージョン固有のファイルを発行フォルダーに発行します。 未署名のセットアップ プログラムは発行プロセスで上書きされません。  
  
11. 顧客側でコマンド プロンプトを開きます。  
  
12. 格納されているディレクトリに変更、 *.exe*ファイル。  
  
13. サインイン、 *.exe*次のコマンドでファイル。  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     たとえば、セットアップ プログラムに署名するには、次のコマンドのいずれかを使用します。  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>関連項目  
 [方法: アプリケーション マニフェストと配置マニフェストに再署名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
