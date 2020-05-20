---
title: Windows 10 高速更新プログラムの管理
titleSuffix: Configuration Manager
description: Configuration Manager では Windows 10 用の高速インストール ファイルがサポートされます。これを使用すると、クライアント上でのダウンロード量を少なくし、インストールに要する時間を短縮できます。
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 11/02/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.openlocfilehash: 4093eafe9f8a337ce322165a529f630a759b365f
ms.sourcegitcommit: bbf820c35414bf2cba356f30fe047c1a34c5384d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81701380"
---
# <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10 更新プログラムに対する高速インストール ファイルの管理

Configuration Manager では Windows 10 更新プログラムに対する高速インストール ファイルがサポートされています。 当月の Windows 10 累積的な品質更新プログラムと前月の更新プログラムの間の変更点だけをダウンロードするようにクライアントを構成してください。 高速インストール ファイルを使用しない場合、Configuration Manager クライアントでは完全な Windows 10 累積的な更新プログラム (以前の月の更新プログラムをすべて含む) が毎月ダウンロードされます。 高速インストール ファイルを使用すると、クライアント上でのダウンロード量を少なくし、インストールに要する時間を短縮できます。

Configuration Manager を使用して、Windows 10 を最新の状態に保つための更新プログラムのコンテンツを管理する方法については、「[Windows 10 更新プログラムの配信の最適化](optimize-windows-10-update-delivery.md)」をご覧ください。  


> [!IMPORTANT]  
> Windows 10 バージョン 1607 では、Windows Update エージェントへの更新を含む OS クライアント サポートを利用できます。 この更新プログラムは 2017 年 4 月 11 日にリリースされた更新プログラムに付属しています。 これらの更新プログラムの詳細については、「[サポート技術情報 4015217](https://support.microsoft.com/kb/4015217)」を参照してください。 今後の更新プログラムでは、高速の活用によりダウンロード量をさらに少なくすることができます。 この更新プログラムが適用されていない以前のバージョンの Windows 10 および Windows 10 バージョン 1607 では、高速インストール ファイルをサポートしていません。  


## <a name="enable-the-site-to-download-express-installation-files-for-windows-10-updates"></a>Windows 10 更新プログラム用の高速インストール ファイルのダウンロードをサイトで有効にする
Windows 10 高速インストール ファイルのメタデータの同期を開始するには、ソフトウェアの更新ポイントのプロパティで同期を有効にします。  

1. Configuration Manager コンソールで、 **[管理]** ワークスペースに移動し、 **[サイトの構成]** を展開して **[サイト]** ノードを選択します。  

2. 中央管理サイトまたはスタンドアロン プライマリ サイトを選択します。  

3. リボンの **[サイト コンポーネントの構成]** をクリックし、 **[ソフトウェアの更新ポイント]** をクリックします。 **[更新ファイル]** タブに切り替えて、 **[すべての承認された更新プログラムのファイルと Windows 10 用高速インストール ファイルの両方をダウンロードする]** を選択します。

> [!NOTE]    
> 高速更新プログラム*のみ*をダウンロードするよう、ソフトウェアの更新ポイント コンポーネントは構成できません。  サイトでは、すべてのファイルに加えて高速インストール ファイルがダウンロードされます。 これにより、コンテンツ ライブラリに格納されるコンテンツと、配布ポイントに配布および格納されるコンテンツの量が増加します。

> [!Tip]  
> ファイルが使用するディスク上の実際の領域を特定するには、ファイルの **[ディスク上のサイズ]** プロパティを確認します。 [ディスク上のサイズ] プロパティは、[サイズ] の値よりも大幅に小さくなるはずです。 詳細については、[Windows 10 更新プログラムの配信の最適化に関する FAQ](optimize-windows-10-update-delivery.md#bkmk_faq) を参照してください。  


## <a name="enable-clients-to-download-and-install-express-installation-files"></a>クライアントが高速インストール ファイルをダウンロードしてインストールできるようにする
クライアント上で高速インストール ファイルのサポートを有効にするには、クライアント設定の **[ソフトウェア更新プログラム]** グループで高速インストール ファイルを有効にします。 この設定により、指定したポートへの高速インストール ファイルのダウンロード要求をリッスンする新しい HTTP リスナーが作成されます。

> [!NOTE]    
> これは、クライアントが配信の最適化またはバックグラウンド インテリジェント転送サービス (BITS) からの要求をリッスンして、配布ポイントから高速コンテンツをダウンロードするのに使用するローカル ポートです。 すべてのトラフィックはローカル コンピューター上にあるため、ファイアウォールでこのポートを開く必要はありません。  

クライアント上でこの機能を有効にするようにクライアント設定を展開すると、当月の Windows 10 累積的な更新プログラムと、前月の更新プログラムとの間の差分のダウンロードが試みられます。 クライアントでは、高速インストール ファイルをサポートする Windows 10 のバージョンが実行されている必要があります。  

1. ソフトウェアの更新ポイント コンポーネントのプロパティで高速インストール ファイルのサポートを有効にします (前の手順を参照)。  

2. Configuration Manager コンソールで、 **[管理]** ワークスペースに移動して、 **[クライアント設定]** を選択します。  

3. 適切なクライアント設定を選択し、リボンの **[プロパティ]** をクリックします。  

4. **[ソフトウェア更新プログラム]** グループを選択します。 **[クライアントでの高速インストール ファイルのインストールを有効にする]** を **[はい]** に設定します。 クライアントで HTTP リスナーが使用するポートを使用して **[高速インストール ファイルのコンテンツをダウンロードするために使用するポート]** を構成します。
    - バージョン 1902 では、 **[Express の更新プログラムのコンテンツをダウンロードするために使用するポート]** が、 **[クライアントが差分コンテンツの要求を受信するために使用するポート]** に変更されました。

## <a name="next-steps"></a>次のステップ

[ソフトウェア更新プログラムの展開](deploy-software-updates.md)