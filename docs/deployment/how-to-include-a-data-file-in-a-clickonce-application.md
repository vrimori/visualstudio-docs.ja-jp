---
title: '方法: ClickOnce アプリケーションにデータ ファイルを含める |Microsoft ドキュメント'
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
ms.openlocfilehash: ced10a16bae0e5892fddec1a79b9f7793b4dac43
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815546"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>方法 : ClickOnce アプリケーションにデータ ファイルを含める
各[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションをインストールするには、アプリケーションが、独自のデータを管理できます先のコンピューターのローカル ディスク上のデータ ディレクトリが割り当てられます。 データ ファイルは、任意の種類のファイルを含めることができます。 テキスト ファイル、XML ファイル、または Microsoft Access データベース (.mdb) ファイルのであってもです。 以下の手順は、任意の種類のデータ ファイルを追加する方法を示して、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe を使用して、データ ファイルを追加するには  
  
1.  データ ファイルをアプリケーションのファイルの残りの部分で、アプリケーション ディレクトリに追加します。  
  
     通常、アプリケーション ディレクトリ ディレクトリとなる、現在のバージョンの配置のラベルが付いた — v1.0.0.0 などです。  
  
2.  データ ファイルの一覧に、アプリケーション マニフェストを更新します。  
  
     `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
     このタスクを実行すると、アプリケーション マニフェストでファイルの一覧を再作成しも自動的にハッシュ署名を生成します。  
  
3.  任意のテキスト エディターまたは XML エディターで、アプリケーション マニフェストを開き、検索、`file`最近追加されたファイルの要素。  
  
     という XML ファイルを追加する場合は`Data.xml`ファイルは次のコード例のようになります。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  属性を追加`type`をこの要素の値を指定して`data`です。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  キー ペアまたは証明書を使用して、アプリケーション マニフェストに再署名してから、配置マニフェストを再度署名します。  
  
     アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
     `mage -s app manifest -cf cert_file -pwd password`
  
     `mage -u deployment manifest -appm app manifest`
  
     `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe を使用して、データ ファイルを追加するには  
  
1.  データ ファイルをアプリケーションのファイルの残りの部分で、アプリケーション ディレクトリに追加します。  
  
2.  通常、アプリケーション ディレクトリ ディレクトリとなる、現在のバージョンの配置のラベルが付いた — v1.0.0.0 などです。  
  
3.  **ファイル** メニューのをクリックして**開く**を開くには、アプリケーション マニフェスト。  
  
4.  選択、**ファイル**タブです。  
  
5.  タブの上部にあるテキスト ボックスで、アプリケーションのファイルを格納するディレクトリを入力し、クリックして**Populate**です。  
  
     データ ファイルは、グリッドに表示されます。  
  
6.  設定、**ファイルの種類**データ ファイルの値**データ**です。  
  
7.  アプリケーション マニフェストを保存し、ファイルを再署名します。  
  
     MageUI.exe は、ファイルを再度署名することを求められます。  
  
8.  配置マニフェストに再署名します。  
  
     アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)