<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ruhsat ve İmalat Takip Sistemi</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .card-header {
            background-color: #0d6efd;
            color: white;
        }
        .navbar-brand {
            font-weight: bold;
        }
        .status-completed {
            background-color: #d4edda;
        }
        .status-inprogress {
            background-color: #fff3cd;
        }
        .status-pending {
            background-color: #f8d7da;
        }
        .status-cancelled {
            background-color: #e2e3e5;
        }
        .table-hover tbody tr:hover {
            cursor: pointer;
            background-color: #f5f5f5;
        }
    </style>
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <div class="container">
            <a class="navbar-brand" href="#">Ruhsat & İmalat Takip</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link active" href="#" data-bs-target="dashboard">Dashboard</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-bs-target="projects">Projeler</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-bs-target="reports">Raporlar</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <div class="container mt-4">
        <!-- Dashboard -->
        <div id="dashboard" class="content-section">
            <div class="row">
                <div class="col-md-3 mb-4">
                    <div class="card text-center">
                        <div class="card-header">Toplam Proje</div>
                        <div class="card-body">
                            <h5 class="card-title">132</h5>
                        </div>
                    </div>
                </div>
                <div class="col-md-3 mb-4">
                    <div class="card text-center status-completed">
                        <div class="card-header">Tamamlanan</div>
                        <div class="card-body">
                            <h5 class="card-title">65</h5>
                        </div>
                    </div>
                </div>
                <div class="col-md-3 mb-4">
                    <div class="card text-center status-inprogress">
                        <div class="card-header">Devam Eden</div>
                        <div class="card-body">
                            <h5 class="card-title">45</h5>
                        </div>
                    </div>
                </div>
                <div class="col-md-3 mb-4">
                    <div class="card text-center status-pending">
                        <div class="card-header">Bekleyen</div>
                        <div class="card-body">
                            <h5 class="card-title">22</h5>
                        </div>
                    </div>
                </div>
            </div>

            <div class="row mt-4">
                <div class="col-md-6">
                    <div class="card">
                        <div class="card-header">İlçe Bazında Dağılım</div>
                        <div class="card-body">
                            <canvas id="districtChart" height="250"></canvas>
                        </div>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="card">
                        <div class="card-header">Proje Türleri</div>
                        <div class="card-body">
                            <canvas id="typeChart" height="250"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Projeler -->
        <div id="projects" class="content-section" style="display: none;">
            <div class="card">
                <div class="card-header d-flex justify-content-between align-items-center">
                    <span>Proje Listesi</span>
                    <div>
                        <select id="districtFilter" class="form-select form-select-sm d-inline-block" style="width: auto;">
                            <option value="">Tüm İlçeler</option>
                            <option value="Beykoz">Beykoz</option>
                            <option value="Ümraniye">Ümraniye</option>
                            <option value="Sancaktepe">Sancaktepe</option>
                        </select>
                        <select id="statusFilter" class="form-select form-select-sm d-inline-block ms-2" style="width: auto;">
                            <option value="">Tüm Durumlar</option>
                            <option value="Tamamlandı">Tamamlandı</option>
                            <option value="Devam Ediyor">Devam Ediyor</option>
                            <option value="Beklemede">Beklemede</option>
                            <option value="İptal">İptal</option>
                        </select>
                        <button class="btn btn-sm btn-primary ms-2" id="addProjectBtn">Yeni Proje</button>
                    </div>
                </div>
                <div class="card-body">
                    <div class="table-responsive">
                        <table class="table table-striped table-hover">
                            <thead>
                                <tr>
                                    <th>Proje Kodu</th>
                                    <th>Proje Adı</th>
                                    <th>İlçe</th>
                                    <th>Metraj</th>
                                    <th>Durum</th>
                                    <th>İşlemler</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>KAVMY</td>
                                    <td>KAVMY Projesi</td>
                                    <td>Beykoz</td>
                                    <td>59 m</td>
                                    <td><span class="badge bg-success">Tamamlandı</span></td>
                                    <td>
                                        <button class="btn btn-sm btn-info">Detay</button>
                                        <button class="btn btn-sm btn-warning">Düzenle</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>SWQMO</td>
                                    <td>SWQMO Projesi</td>
                                    <td>Beykoz</td>
                                    <td>70 m</td>
                                    <td><span class="badge bg-success">Tamamlandı</span></td>
                                    <td>
                                        <button class="btn btn-sm btn-info">Detay</button>
                                        <button class="btn btn-sm btn-warning">Düzenle</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>UMKVA</td>
                                    <td>UMKVA Projesi</td>
                                    <td>Ümraniye</td>
                                    <td>785 m</td>
                                    <td><span class="badge bg-warning text-dark">Devam Ediyor</span></td>
                                    <td>
                                        <button class="btn btn-sm btn-info">Detay</button>
                                        <button class="btn btn-sm btn-warning">Düzenle</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>SANEA</td>
                                    <td>SANEA Projesi</td>
                                    <td>Sancaktepe</td>
                                    <td>627 m</td>
                                    <td><span class="badge bg-danger">Beklemede</span></td>
                                    <td>
                                        <button class="btn btn-sm btn-info">Detay</button>
                                        <button class="btn btn-sm btn-warning">Düzenle</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- Raporlar -->
        <div id="reports" class="content-section" style="display: none;">
            <div class="card">
                <div class="card-header">Raporlar</div>
                <div class="card-body">
                    <div class="row mb-4">
                        <div class="col-md-6">
                            <div class="card">
                                <div class="card-header">Metraj Raporu</div>
                                <div class="card-body">
                                    <canvas id="metrajChart" height="200"></canvas>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="card">
                                <div class="card-header">Maliyet Raporu</div>
                                <div class="card-body">
                                    <canvas id="costChart" height="200"></canvas>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">Detaylı Rapor</div>
                        <div class="card-body">
                            <div class="row mb-3">
                                <div class="col-md-4">
                                    <label class="form-label">Başlangıç Tarihi</label>
                                    <input type="date" class="form-control">
                                </div>
                                <div class="col-md-4">
                                    <label class="form-label">Bitiş Tarihi</label>
                                    <input type="date" class="form-control">
                                </div>
                                <div class="col-md-4">
                                    <label class="form-label">&nbsp;</label>
                                    <button class="btn btn-primary form-control">Raporu Oluştur</button>
                                </div>
                            </div>
                            <div class="table-responsive">
                                <table class="table table-striped">
                                    <thead>
                                        <tr>
                                            <th>İlçe</th>
                                            <th>Proje Sayısı</th>
                                            <th>Toplam Metraj</th>
                                            <th>Ortalama Maliyet</th>
                                            <th>Tamamlanma Oranı</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>Beykoz</td>
                                            <td>40</td>
                                            <td>5,842 m</td>
                                            <td>125,000 ₺</td>
                                            <td>65%</td>
                                        </tr>
                                        <tr>
                                            <td>Ümraniye</td>
                                            <td>60</td>
                                            <td>8,756 m</td>
                                            <td>98,500 ₺</td>
                                            <td>45%</td>
                                        </tr>
                                        <tr>
                                            <td>Sancaktepe</td>
                                            <td>32</td>
                                            <td>4,321 m</td>
                                            <td>112,300 ₺</td>
                                            <td>75%</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Navigasyon işlevselliği
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Tüm içerikleri gizle
                document.querySelectorAll('.content-section').forEach(section => {
                    section.style.display = 'none';
                });
                
                // Aktif sekme stillerini güncelle
                document.querySelectorAll('.nav-link').forEach(navLink => {
                    navLink.classList.remove('active');
                });
                this.classList.add('active');
                
                // İlgili içeriği göster
                const target = this.getAttribute('data-bs-target');
                document.getElementById(target).style.display = 'block';
            });
        });

        // Grafikleri oluştur
        document.addEventListener('DOMContentLoaded', function() {
            // İlçe bazında dağılım grafiği
            const districtCtx = document.getElementById('districtChart').getContext('2d');
            new Chart(districtCtx, {
                type: 'pie',
                data: {
                    labels: ['Beykoz', 'Ümraniye', 'Sancaktepe'],
                    datasets: [{
                        data: [40, 60, 32],
                        backgroundColor: ['#4e73df', '#1cc88a', '#36b9cc']
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false
                }
            });

            // Proje türleri grafiği
            const typeCtx = document.getElementById('typeChart').getContext('2d');
            new Chart(typeCtx, {
                type: 'bar',
                data: {
                    labels: ['FiberSite', 'Bireysel', 'Kurumsal'],
                    datasets: [{
                        label: 'Proje Sayısı',
                        data: [95, 25, 12],
                        backgroundColor: '#4e73df'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });

            // Metraj grafiği
            const metrajCtx = document.getElementById('metrajChart').getContext('2d');
            new Chart(metrajCtx, {
                type: 'line',
                data: {
                    labels: ['Ocak', 'Şubat', 'Mart', 'Nisan', 'Mayıs', 'Haziran'],
                    datasets: [{
                        label: 'Aylık Metraj (m)',
                        data: [1250, 1950, 2100, 2780, 1850, 2300],
                        borderColor: '#4e73df',
                        tension: 0.1,
                        fill: false
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false
                }
            });

            // Maliyet grafiği
            const costCtx = document.getElementById('costChart').getContext('2d');
            new Chart(costCtx, {
                type: 'bar',
                data: {
                    labels: ['Beykoz', 'Ümraniye', 'Sancaktepe'],
                    datasets: [{
                        label: 'Ortalama Maliyet (₺)',
                        data: [125000, 98500, 112300],
                        backgroundColor: ['#4e73df', '#1cc88a', '#36b9cc']
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false
                }
            });
        });
    </script>
</body>
</html>
