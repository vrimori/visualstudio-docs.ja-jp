---
title: '方法: 符号 SignTool.exe (ClickOnce) を持つファイルをセットアップする |Microsoft ドキュメント'
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
ms.openlocfilehash: dc4dc7b2f96b1d36e91e8114458a7a8e9f3231f3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566122"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>方法: SignTool.exe を使用してセットアップ ファイルに署名する (ClickOnce)
SignTool.exe を使用して、セットアップ プログラム (setup.exe) に署名できます。 このプロセスによって、改ざんされたファイルがエンド ユーザーのコンピューターにインストールされないようにすることができます。  
  
 既定で、ClickOnce には複数の署名されたマニフェストと、1 つの署名されたセットアップ プログラムがあります。 ただし、後でセットアップ プログラムのパラメーターを変更する場合、セットアップ プログラムに後で署名する必要があります。 セットアップ プログラムの署名後にパラメーターを変更すると、署名が破損します。  
  
 次の手順では、未署名のマニフェストと未署名のセットアップ プログラムを生成します。 次に、ClickOnce の署名を Visual Studio で有効にし、署名されたマニフェストを生成します。 セットアップ プログラムは未署名のままなので、ユーザーは自分の証明書を使用して実行可能ファイルに署名できます。  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>未署名のセットアップ プログラムを生成し、後で署名するには  
  
1.  マニフェストに署名する証明書を開発用コンピューターにインストールします。  
  
2.  プロジェクトを選択**ソリューション エクスプ ローラー**です。  
  
3.  **プロジェクト** メニューのをクリックして*ProjectName* **プロパティ**です。  
  
4.  **署名** ページでクリア**ClickOnce マニフェストに署名**です。  
  
5.  **発行**] ページで [**の前提条件**です。  
  
6.  すべての前提条件が選択されていることを確認し、をクリックして**OK**です。  
  
7.  **発行**] ページで、発行設定を確認してをクリックして **[今すぐ発行**です。  
  
     ソリューションは、未署名のアプリケーション マニフェスト、未署名の配置マニフェスト、バージョン固有のファイル、および未署名のセットアップ プログラムを発行フォルダーに発行します。  
  
8.  **発行**] ページで [**の前提条件**です。  
  
9. **の前提条件**ダイアログ ボックスで、クリア**前提条件コンポーネントをインストールするセットアップ プログラムを作成する**です。  
  
10. **発行**] ページで、発行設定を確認してをクリックして **[今すぐ発行**です。  
  
     ソリューションは、署名済みのアプリケーション マニフェスト、署名済みの配置マニフェスト、およびバージョン固有のファイルを発行フォルダーに発行します。 未署名のセットアップ プログラムは発行プロセスで上書きされません。  
  
11. 顧客側でコマンド プロンプトを開きます。  
  
12. .exe ファイルを含むディレクトリに移動します。  
  
13. 次のコマンドで .exe ファイルに署名します。  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     たとえば、セットアップ プログラムに署名するには、次のコマンドのいずれかを使用します。  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>関連項目  
 [方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)