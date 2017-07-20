---
title: "Visual Studio の展開時にプロダクト キーを自動的に適用する | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio の展開時にプロダクト キーを自動的に適用する
Visual Studio の配置を自動化するために使用されるスクリプトの一部として、プログラム的にプロダクト キーを適用することができます。 プロダクト キーは、Visual Studio のインストール中またはインストール完了後に、プログラム的にデバイスで設定できます。

## <a name="apply-the-license-after-installation"></a>インストール後にライセンスを適用する
 ターゲット コンピューターにある `StorePID.exe` ユーティリティをサイレント モードで使用して、インストールされているバージョンの Visual Studio をプロダクト キーでアクティブにすることができます。 `StorePID.exe` は次の既定の場所に Visual Studio 2017 をインストールするユーティリティ プログラムです。 <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 System Center エージェントまたは管理者特権でのコマンド プロンプトのいずれかを使用することにより、昇格された特権で `StorePID.exe` を実行します。その際、プロダクト キー (ダッシュを含む) と Microsoft 製品コード (MPC) を後ろに付けます。 プロダクト キーには、ダッシュ (-) を含めないください。

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 以下は Visual Studio 2017 Enterprise にライセンスを適用するサンプル コマンド ラインです。MPC は 08860 で、製品キーは `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` です。既定の場所にインストールするものと想定しています。

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 次の表に、Visual Studio の各エディションの MPC コードを一覧します。

| Visual Studio エディション                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

`StorePID.exe` が正常にプロダクト キーを適用した場合は `%ERRORLEVEL%` として 0 を返します。 エラーが発生した場合、エラーの状態に基づいてコードが返されます。

| エラー                     | コード |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>関連項目
 * [Visual Studio のインストール](../install/install-visual-studio.md)
 * [Visual Studio のオフライン インストールを作成する](../install/create-an-offline-installation-of-visual-studio.md)

