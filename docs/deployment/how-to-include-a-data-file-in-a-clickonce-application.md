---
title: '方法: ClickOnce アプリケーションにデータ ファイルを含める |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfba7612ec0e019b8c8dfa7c7406435b6e43e6cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917922"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>方法: ClickOnce アプリケーションにデータ ファイルを含める
各[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションをインストールするには、アプリケーションが独自のデータを管理できる先のコンピューターのローカル ディスク上のデータ ディレクトリが割り当てられます。 データ ファイルは、任意の種類のファイルを含めることができます。 テキスト ファイル、XML ファイル、または Microsoft Access データベース (*.mdb*) ファイル。 次の手順に任意の型のデータ ファイルを追加する方法を示して、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe を使用して、データ ファイルを追加するには  
  
1. アプリケーションのファイルの残りの部分で、アプリケーション ディレクトリにデータ ファイルを追加します。  
  
    通常、アプリケーションのディレクトリは、展開の現在のバージョン ラベルが付いた、ディレクトリに — v1.0.0.0 など。  
  
2. データ ファイルの一覧に、アプリケーション マニフェストを更新します。  
  
    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
    このタスクを実行すると、アプリケーション マニフェストでファイルの一覧を再作成しも自動的にハッシュ署名を生成します。  
  
3. 任意のテキスト エディターまたは XML エディターで、アプリケーション マニフェストを開き、検索、`file`最近追加されたファイルの要素。  
  
    という XML ファイルを追加する場合は`Data.xml`ファイルは次のコード例のようになります。  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. 属性を追加`type`この要素の値を入力して`data`します。  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. 証明書またはキー ペアを使用して、アプリケーション マニフェストに再署名し、配置マニフェストを再署名します。  
  
    アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
    `mage -s app manifest -cf cert_file -pwd password`
  
    `mage -u deployment manifest -appm app manifest`
  
    `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe を使用してデータ ファイルを追加するには  
  
1.  アプリケーションのファイルの残りの部分で、アプリケーション ディレクトリにデータ ファイルを追加します。  
  
2.  通常、アプリケーションのディレクトリは、展開の現在のバージョン ラベルが付いた、ディレクトリに — v1.0.0.0 など。  
  
3.  **ファイル** メニューのをクリックして**開く**をアプリケーション マニフェストを開きます。  
  
4.  選択、**ファイル**タブ。  
  
5.  タブの上部にあるテキスト ボックスで、アプリケーションのファイルを含むディレクトリを入力し、クリックして**Populate**します。  
  
     データ ファイルは、グリッドに表示されます。  
  
6.  設定、**ファイルの種類**データ ファイルの値**データ**します。  
  
7.  アプリケーション マニフェストを保存し、ファイルを再署名します。  
  
     *MageUI.exe*ファイルに再署名するように求められます。  
  
8.  配置マニフェストに再署名します。  
  
     アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションにおけるローカルおよびリモート データにアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)